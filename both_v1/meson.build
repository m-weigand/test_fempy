project('pycrtomomod',
        ['c', 'fortran'],
        version : '0.1',
        meson_version: '>= 1.1.0',
        default_options : [
                            'warning_level=1',
                            'buildtype=release'
                          ])

# not yet sure if we need the following three lines
add_project_link_arguments('-Wl,-ld_classic', language : ['c', 'cpp', 'fortran'])
cc = meson.get_compiler('c')
ff = meson.get_compiler('fortran')


subdir('lib/crtomo_tests')
subdir('lib/crtomo_wrapper')
subdir('pycrmod_v2')
subdir('pycrtomo_v3')
subdir('pycutmck_v1')
