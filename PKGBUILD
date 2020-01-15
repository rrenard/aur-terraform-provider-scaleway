pkgname=terraform-provider-scaleway
pkgver=1.13.0
pkgrel=1
pkgdesc="Terraform Scaleway provider"
url="https://github.com/terraform-providers/terraform-provider-scaleway"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/terraform-providers"
depends=('terraform')
source=("https://github.com/terraform-providers/terraform-provider-scaleway/archive/v${pkgver}.tar.gz")
sha256sums=('b1cf86c0bd8c35e87f3b27e16f98df4b94e271b361fbde9f7737597841d5bc66')

prepare() {
    mkdir -p "$srcdir/src/$_gourl"
    rm -rf "${srcdir}/src/$_gourl/$pkgname"
    mv -f "$pkgname-$pkgver" "$srcdir/src/$_gourl/$pkgname"
    msg2 "Fetching dependencies"
    cd "$srcdir/src/$_gourl/$pkgname"
}


build() {
    msg2 "Build program"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" GOBIN="$srcdir/bin" PATH="$srcdir/bin:$PATH" make
}


package() {
    cd "$srcdir/bin"
    install -Dm755 $pkgname "$pkgdir/usr/bin/$pkgname"
}

