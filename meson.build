project('libutil', 'c',
  version: '0.2.0',
  license: 'MPL-2.0',
  meson_version: '>=0.64.0',
  default_options: ['warning_level=2', 'c_std=c99'])

if not meson.is_subproject()
  subdir('meson/toolchain')
else
  add_project_arguments('-masm-syntax-unified', language: 'c')
endif

sources = [
  'src/assert.c',
  'src/bit.s',
  'src/debug.s',
  'src/log.c',
  'src/profile.s',
  'src/rand.s',
  'src/simd.s',
]

includes = ['include']

libutil = static_library(
  'util',
  sources,
  include_directories: includes + ['src'],
  install: true)

install_subdir('include/util', install_dir: get_option('includedir'))

libutil_dep = declare_dependency(
  include_directories: includes,
  link_with: libutil)

meson.override_dependency('libutil', libutil_dep)
