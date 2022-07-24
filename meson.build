project('adaptivebinarize', 'cpp',
  default_options: ['buildtype=release', 'warning_level=2', 'b_lto=true', 'b_ndebug=if-release', 'cpp_std=c++17'],
  license: 'MIT',
  meson_version: '>=0.51.0',
  version: '14'
)

cxx = meson.get_compiler('cpp')

gcc_syntax = cxx.get_argument_syntax() == 'gcc'

if gcc_syntax
  vapoursynth_dep = dependency('vapoursynth', version: '>=55').partial_dependency(compile_args: true, includes: true)
  install_dir = vapoursynth_dep.get_variable(pkgconfig: 'libdir') / 'vapoursynth'
else
  vapoursynth_dep = []
  install_dir = get_option('libdir') / 'vapoursynth'
endif

sources = [
  'src/adaptivebinarize.cpp'
]

libs = []

shared_module('adaptivebinarize', sources,
  dependencies: vapoursynth_dep,
  link_with: libs,
  install: true,
  install_dir: install_dir,
  gnu_symbol_visibility: 'hidden'
)
