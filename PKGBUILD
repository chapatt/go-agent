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
	  'c374dff852906607c92c0fb04dd246af97b5552f'
	  '337a91d0e5c562f4c8632a59a2fa342dc4c8492b')
depends=('java-runtime>=8')

package()
{
	install -Dm644 go-agent.service \
		"$pkgdir"/usr/lib/systemd/system/go-agent.service
	install -Dm644 go-agent.sysusers \
		"$pkgdir"/usr/lib/sysusers.d/go-agent.conf
	install -Dm644 go-agent.tmpfiles \
		"$pkgdir"/usr/lib/tmpfiles.d/go-agent.conf

	install -dm755 "$pkgdir"/usr/share/go-agent/
	install -dm755 -o 8155 -g 8155 "$pkgdir"/var/lib/go-agent/
	install -dm755 -o 8155 -g 8155 "$pkgdir"/var/lib/go-agent/config/

	cd $pkgname-$pkgver/
	install -Dm644 go-agent.default "$pkgdir"/etc/default/go-agent
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	install -Dm644 agent-bootstrapper.jar \
		"$pkgdir"/usr/share/$pkgname/agent-bootstrapper.jar
	install -Dm755 agent.sh "$pkgdir"/usr/share/$pkgname/agent.sh
	install -Dm755 stop-agent.sh "$pkgdir"/usr/share/$pkgname/stop-agent.sh
}
