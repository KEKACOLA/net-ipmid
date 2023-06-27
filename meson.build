project(
  'netipmid',
  'cpp',
  version: '0.1',
  meson_version: '>=0.57.0',
  default_options: [
    'warning_level=3',
    'cpp_std=c++17',
  ])

install_data(
    'netipmid',
    install_mode: 'r-xr-xr-x',
    install_dir: get_option('bindir')
)

systemd_dep = dependency('systemd')
systemd_system_unit_dir = systemd_dep.get_variable(pkgconfig : 'systemdsystemunitdir')

unit_files = [
    'phosphor-ipmi-net@.service',
    'phosphor-ipmi-net@.socket'
]

configure_file(
  input: 'phosphor-ipmi-net@.service',
  output: 'phosphor-ipmi-net@.service',
  configuration: {
    'SYSTEMD_TARGET': 'multi-user.target',
  },
  install: true,
  install_dir: dependency('systemd').get_variable(
    pkgconfig: 'systemdsystemunitdir'))

configure_file(
  input: 'phosphor-ipmi-net@.socket',
  output: 'phosphor-ipmi-net@.socket',
  configuration: {
    'SYSTEMD_TARGET': 'multi-user.target',
  },
  install: true,
  install_dir: dependency('systemd').get_variable(
    pkgconfig: 'systemdsystemunitdir'))