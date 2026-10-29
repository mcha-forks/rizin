python_exe = find_program('python3', required: false)
tree_sitter_bin = find_program('tree-sitter', required: false)
node_bin = find_program('node', required: false)
if python_exe.found() and tree_sitter_bin.found() and node_bin.found() and tree_sitter_dep.type_name() != 'internal'
  parser_c = custom_target('parser_src_c',
    command: [python_exe, tree_sitter_wrap_py, tree_sitter_bin, '@OUTDIR@/..', '@INPUT@'],
    input: [grammar_js],
    output: 'parser.c',
  )
else
  parser_c = files('parser.c')
endif

shell_parser_files = [files('scanner.c'), parser_c]
shell_parser_inc = [include_directories('tree_sitter')]
