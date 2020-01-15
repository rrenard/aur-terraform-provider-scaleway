pkgname=terraform-provider-scaleway
pkgver=1.10.0
pkgrel=1
pkgdesc="Terraform Scaleway provider"
url="https://github.com/terraform-providers/terraform-provider-scaleway"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/terraform-providers"
depends=('terraform')
source=("https://github.com/terraform-providers/terraform-provider-scaleway/archive/v${pkgver}.tar.gz")
sha256sums=('7b0b26c95430dbbe7e4088235b1801c5f2811b0bee32e6d5c0dc8c6907ccffa3')

prepare() {
    mkdir -p "$srcdir/src/$_gourl"
    rm -rf "${srcdir}/src/$_gourl/$pkgname"
    mv -f "$pkgname-$pkgver" "$srcdir/src/$_gourl/$pkgname"
    msg2 "Fetching dependencies"
    cd "$srcdir/src/$_gourl/$pkgname"
    GOPATH="$srcdir" GOBIN="$srcdir/bin" go get -u github.com/hashicorp/terraform
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

