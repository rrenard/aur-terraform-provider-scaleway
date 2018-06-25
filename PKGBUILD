pkgname=terraform-provider-scaleway
pkgver=1.4.1
pkgrel=1
pkgdesc="Terraform Scaleway provider"
url="https://github.com/terraform-providers/terraform-provider-scaleway"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/terraform-providers"
depends=('terraform')
source=("https://github.com/terraform-providers/terraform-provider-scaleway/archive/v${pkgver}.tar.gz")
sha256sums=('f851a119f83914abf13cc5f8535f63945b585829d1bbfb9a07d498d4a4d43e01')


prepare() {
    mkdir -p "$srcdir/src/$_gourl"
    rm -rf "${srcdir}/src/$_gourl/$pkgname"
    mv -f "$pkgname-$pkgver" "$srcdir/src/$_gourl/$pkgname"
    msg2 "Fetching dependencies"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" go get -u github.com/hashicorp/terraform
}


build() {
    msg2 "Build program"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" PATH="$srcdir/bin:$PATH" make 
}


package() {
    cd "$srcdir/bin"
    install -Dm755 $pkgname "$pkgdir/usr/bin/$pkgname"
}

