bees_version_c = vcs_tag(
  input: 'bees-version.c.in',
  output: 'bees-version.c',
  replace_string: '@VERSION@',
)

bees_usage_c = custom_target(
  input: 'bees-usage.txt',
  output: 'bees-usage.c',
  command: [ python, files('bees-usage.py'), '@INPUT@', '@OUTPUT@' ],
)

executable(
  'bees',
  [
    'bees.cc',
    'bees-context.cc',
    'bees-hash.cc',
    'bees-resolve.cc',
    'bees-roots.cc',
    'bees-thread.cc',
    'bees-trace.cc',
    'bees-types.cc',
    bees_version_c,
    bees_usage_c,
  ],
  dependencies: [ thread_dep ],
  implicit_include_directories: false,
  include_directories: [ inc ],
  install: true,
  install_dir: beeslibdir,
  link_with: [ crucible_lib ],
)

executable(
  'fiemap',
  [ 'fiemap.cc' ],
  implicit_include_directories: false,
  include_directories: [ inc ],
  install: get_option('tools'),
  link_with: [ crucible_lib ],
)

executable(
  'fiewalk',
  [ 'fiewalk.cc' ],
  implicit_include_directories: false,
  include_directories: [ inc ],
  install: get_option('tools'),
  install_dir: get_option('sbindir'),
  link_with: [ crucible_lib ],
)
