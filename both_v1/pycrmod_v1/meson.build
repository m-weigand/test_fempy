project('pycrmod',
        ['c', 'fortran'],
        version : '0.1',
        meson_version: '>= 1.1.0',
        default_options : [
                            'warning_level=1',
                            'buildtype=release'
                          ],
  )
add_global_link_arguments(
  '-static-libgcc',
  #'-static',
  language: 'c',
)
fc = meson.get_compiler('fortran')

# py = import('python').find_installation('''/home/mweigand/.virtualenvs/invmod/bin/python''', pure: false)
py = import('python').find_installation()
py_dep = py.dependency()

incdir_numpy = run_command(py,
  ['-c', 'import os; os.chdir(".."); import numpy; print(numpy.get_include())'],
  check : true
).stdout().strip()

incdir_f2py = run_command(py,
    ['-c', 'import os; os.chdir(".."); import numpy.f2py; print(numpy.f2py.get_include())'],
    check : true
).stdout().strip()

inc_np = include_directories(incdir_numpy)
np_dep = declare_dependency(include_directories: inc_np)

incdir_f2py = incdir_numpy / '..' / '..' / 'f2py' / 'src'
inc_f2py = include_directories(incdir_f2py)
fortranobject_c = incdir_f2py / 'fortranobject.c'

inc_np = include_directories(incdir_numpy, incdir_f2py)
# gh-25000
quadmath_dep = fc.find_library('quadmath', required: false)




py.extension_module('pycrmod',
                     [
                     '''src/my_git_version.h''',
                     '''src/crerror.h''',
                     '''src/elemmod.f90''',
                     '''src/alloci.f90''',
                     '''src/get_error.f90''',
                     '''src/tic_toc.f90''',
                     '''src/femmod.f90''',
                     '''src/datmod.f90''',
                     '''src/sigmamod.f90''',
                     '''src/electrmod.f90''',
                     '''src/modelmod.f90''',
                     '''src/relem.f90''',
                     '''src/relectr.f90''',
                     '''src/rdatm.f90''',
                     '''src/bsytop.f90''',
                     '''src/elem1.f90''',
                     '''src/elem3.f90''',
                     '''src/elem5.f90''',
                     '''src/elem8.f90''',
                     '''src/bessi0.f90''',
                     '''src/bessi1.f90''',
                     '''src/bessk0.f90''',
                     '''src/bessk1.f90''',
                     '''src/beta.f90''',
                     '''src/precal.f90''',
                     '''src/rrandb.f90''',
                     '''src/randb.f90''',
                     '''src/randdc.f90''',
                     '''src/refsig.f90''',
                     '''src/get_unit.f90''',
                     '''src/make_noise.f90''',
                     '''src/invmod.f90''',
                     '''src/rtrafo.f90''',
                     '''src/wkpot.f90''',
                     '''src/intcha.f90''',
                     '''src/filpat.f90''',
                     '''src/wpot.f90''',
                     '''src/bpot.f90''',
                     '''src/bkfak.f90''',
                     '''src/rsigma.f90''',
                     '''src/bvolt.f90''',
                     '''src/wavenmod.f90''',
                     '''src/vre.f90''',
                     '''src/bsens.f90''',
                     '''src/wsens.f90''',
                     '''src/randbmod.f90''',
                     '''src/errmod.f90''',
                     '''src/konvmod.f90''',
                     '''src/get_git_ver.f90''',
                     '''src/ompmod.f90''',
                     '''src/gammln.f90''',
                     '''src/gaulag.f90''',
                     '''src/gauleg.f90''',
                     '''src/kompab.f90''',
                     '''src/kompadc.f90''',
                     '''src/potana.f90''',
                     '''src/chold.f90''',
                     '''src/choldc.f90''',
                     '''src/chol.f90''',
                     '''src/rwaven.f90''',
                     '''src/randb2.f90''',
                     '''src/kompb.f90''',
                     '''src/wdatm.f90''',
                     '''src/scalab.f90''',
                     '''src/output_fempy.f90''',
                     '''src/fempy.f90''',
                     '''pycrmodmodule.c''',
                     '''src/pycrmod-f2pywrappers2.f90''',
                     fortranobject_c
                     ],
                     include_directories: [
                     inc_np,

                     ],
                     dependencies : [
                     py_dep,
                     quadmath_dep,
                     dependency('openmp'),


                     ],

                     install : true)
