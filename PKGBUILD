# Maintainer: Chase Patterson <chapatt at gmail dot com>
pkgname=go-agent
pkgver=17.12.0
pkgrel=1
pkgdesc='GoCD (continuous delivery) agent'
arch=('any')
url='http://gocd.org'
license=('Apache')
source=("go-agent-17.12.0-5626.zip::https://download.gocd.org/binaries/17.12.0-5626/generic/go-agent-17.12.0-5626.zip"
	'go-agent.service'
	'go-agent.sysusers'
	'go-agent.tmpfiles')
sha1sums=('fb13b25b01e08342c0979e0367ddf48ca346ff98'
	  '412ff92811025f962250ff956258f562b364019a'
	  'd06d856b7284b2e0884e48373de19a58a1282002'
	  '109387b7901e7861bbc4c2f91730cc767bfb7ee3')
depends=('java-runtime>=8')

package()
{
	install -Dm644 go-agent.service \
		"$pkgdir"/usr/lib/systemd/system/$pkgname.service
	install -Dm644 go-agent.sysusers \
		"$pkgdir"/usr/lib/sysusers.d/$pkgname.conf
	install -Dm644 go-agent.tmpfiles \
		"$pkgdir"/usr/lib/tmpfiles.d/$pkgname.conf

	install -dm755 "$pkgdir"/usr/share/$pkgname/

	cd $pkgname-$pkgver/
	install -Dm644 go-agent.default "$pkgdir"/etc/default/go-agent
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	install -Dm644 agent-bootstrapper.jar \
		"$pkgdir"/usr/share/$pkgname/agent-bootstrapper.jar
	install -Dm755 agent.sh "$pkgdir"/usr/share/$pkgname/agent.sh
	install -Dm755 stop-agent.sh "$pkgdir"/usr/share/$pkgname/stop-agent.sh
}
