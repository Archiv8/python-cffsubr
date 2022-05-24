#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-cffsubr/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-cffsubr/discussions>

_langname="python"
_relname="cffsubr"

pkgname="${_langname}-${_relname}"
pkgver=0.2.9.post1
pkgrel=1
pkgdesc=_ta"Standalone CFF subroutinizer based on AFDKO tx_ta"
arch=(
  "x86_64"
)
url="https://github.com/adobe-type-tools/cffsubr"
license=(
  "Apache"
)
depends=(
  "python"
  "python-fonttools"
)
makedepends=(
  "python-setuptools-git-ls-files"
  "python-setuptools-scm"
)
checkdepends=(
  "python-pytest"
)
_tarname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_tarname}.tar.gz"
)
sha512sums=(
  "8c83001010951990d4e0dcecd1820e0f469042518c63cf82b66425c383b640f525f253b10f16ad587e9492a9aed070715d776d909ab4e897c99a22a7678f38a7"
)

build() {

  cd "${_tarname}"

  python setup.py build_ext --inplace

  python setup.py build
}

check() {

  cd "${_tarname}"

  PYTHONPATH=src pytest tests
}

package() {

  cd "${_tarname}"

  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
}
