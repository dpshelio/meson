project('llvmtest', ['c', 'cpp'], default_options : ['c_std=c99'])

llvm_dep = dependency(
  'llvm',
  modules : ['bitwriter', 'asmprinter', 'executionengine', 'target',
             'mcjit', 'nativecodegen'],
  required : true,
)

d = dependency('llvm', modules : 'not-found', required : false)
assert(d.found() == false, 'not-found llvm module found')

d = dependency('llvm', version : '<0.1', required : false)
assert(d.found() == false, 'ancient llvm module found')

executable('sum', 'sum.c',  dependencies : [
  llvm_dep,
  dependency('zlib'),
  meson.get_compiler('c').find_library('dl', required : false),
  dependency('tinfo'),
  ])
