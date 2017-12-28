pkgname=perl-io-tty
pkgver=1.12
pkgrel=1
pkgdesc="Provide an interface to TTYs and PTYs"
arch=('x86_64')
url="http://search.cpan.org/dist/IO-Tty/"
license=("GPL" "PerlArtistic")
depends=('glibc')
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/T/TO/TODDR/IO-Tty-$pkgver.tar.gz")
md5sums=('11695a1a516b3bd1b90ce75ff0ce3e6d')

build() {
  cd "$srcdir"/IO-Tty-$pkgver
  PERL_MM_USE_DEFAULT=1 perl Makefile.PL INSTALLDIRS=vendor
  make
}
package() {
  cd "$srcdir"/IO-Tty-$pkgver
  make install DESTDIR="$pkgdir"
  find "$pkgdir" -name '.packlist' -delete
  find "$pkgdir" -name '*.pod' -delete
# template start; name=perl-binary-module-dependency; version=1;
if [[ $(find "$pkgdir/usr/lib/perl5/" -name "*.so") ]]; then
	_perlver_min=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]);')
	_perlver_max=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]+1);')
	depends+=("perl>=$_perlver_min" "perl<$_perlver_max")
fi
# template end;
}