pkgname=terraform-provider-scaleway
pkgver=1.6.0
pkgrel=1
pkgdesc="Terraform Scaleway provider"
url="https://github.com/terraform-providers/terraform-provider-scaleway"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/terraform-providers"
depends=('terraform')
source=("https://github.com/terraform-providers/terraform-provider-scaleway/archive/v${pkgver}.tar.gz")
sha256sums=('a508b4cc7aaf4bcd8f93b8ba6e2e28c46a40f8478fe9f0e4213ffc2bab0039bc')


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

