pkgname=terraform-provider-scaleway
pkgver=1.8.0
pkgrel=1
pkgdesc="Terraform Scaleway provider"
url="https://github.com/terraform-providers/terraform-provider-scaleway"
arch=("i686" "x86_64")
license=("MPL2")
makedepends=("go" "git")
_gourl="github.com/terraform-providers"
depends=('terraform')
source=("https://github.com/terraform-providers/terraform-provider-scaleway/archive/v${pkgver}.tar.gz")
sha256sums=('a3af9e7b7a57c2729fc2bb3440c6ded7091821d688cdd9e12e9533d61728d001')


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

