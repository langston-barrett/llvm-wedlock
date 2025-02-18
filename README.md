# llvm-wedlock

A fork of LLVM 7 and LLVM 10 with the Wedlock pass, used by MATE.

## Usage

The Wedlock pass currently builds in Docker:

```bash
docker build -t llvm-wedlock .
docker run --rm -it llvm-wedlock /bin/bash
```

Within Docker:

```bash
# Either .bc or .ll will work
/chess/llvm/bin/llc -wedlock -wedlock-output foo.wedlock.jsonl -o foo.s foo.bc
```

## Build Instructions

**NOTE**: These instructions may be stale.

Build with:
```bash
mkdir build
cd build
cmake \
 -DCMAKE_BUILD_TYPE=${BUILD_TYPE} \
 -DCLANG_ENABLE_ARCMT=False \
 -DCLANG_BUILD_TOOLS=False \
 -DCLANG_ENABLE_STATIC_ANALYZER=False \
 -DCLANG_INSTALL_SCANVIEW=False \
 -DCLANG_INSTALL_SCANBUILD=False \
 -DCLANG_PLUGIN_SUPPORT=False \
 -DCLANG_TOOL_ARCMT_TEST_BUILD=False \
 -DCLANG_TOOL_CLANG_CHECK_BUILD=False \
 -DCLANG_TOOL_CLANG_DIFF_BUILD=False \
 -DCLANG_TOOL_CLANG_FORMAT_BUILD=False \
 -DCLANG_TOOL_CLANG_FORMAT_VS_BUILD=False \
 -DCLANG_TOOL_CLANG_FUNC_MAPPING_BUILD=False \
 -DCLANG_TOOL_CLANG_FUZZER_BUILD=False \
 -DCLANG_TOOL_CLANG_IMPORT_TEST_BUILD=False \
 -DCLANG_TOOL_CLANG_OFFLOAD_BUNDLER_BUILD=False \
 -DCLANG_TOOL_CLANG_REFACTOR_BUILD=False \
 -DCLANG_TOOL_CLANG_RENAME_BUILD=False \
 -DCLANG_TOOL_C_ARCMT_TEST_BUILD=False \
 -DCLANG_TOOL_C_INDEX_TEST_BUILD=False \
 -DCLANG_TOOL_DIAGTOOL_BUILD=False \
 -DCLANG_TOOL_DRIVER_BUILD=False \
 -DCLANG_TOOL_HANDLE_CXX_BUILD=False \
 -DCLANG_TOOL_HANDLE_LLVM_BUILD=False \
 -DCLANG_TOOL_LIBCLANG_BUILD=False \
 -DCLANG_TOOL_SCAN_BUILD_BUILD=False \
 -DCLANG_TOOL_SCAN_VIEW_BUILD=False \
 -DCLANG_TOOLS_EXTRA_INCLUDE_DOCS=False \
 -DLLVM_ENABLE_BINDINGS=False \
 -DLLVM_ENABLE_IDE=False \
 -DLLVM_ENABLE_MODULE_DEBUGGING=False \
 -DLLVM_ENABLE_OCAMLDOC=False \
 -DLLVM_ENABLE_PROJECTS=clang \
 -DLLVM_INCLUDE_DOCS=False \
 -DLLVM_INCLUDE_EXAMPLES=False \
 -DLLVM_INCLUDE_GO_TESTS=False \
 -DLLVM_INCLUDE_RUNTIMES=False \
 -DLLVM_INCLUDE_TESTS=False \
 -DLLVM_INCLUDE_UTILS=False \
 -DLLVM_POLLY_BUILD=False \
 -DLLVM_POLLY_LINK_INTO_TOOLS=False \
 -DLLVM_TARGETS_TO_BUILD="X86" \
 -DLLVM_TOOL_BUGPOINT_BUILD=False \
 -DLLVM_TOOL_BUGPOINT_PASSES_BUILD=False \
 -DLLVM_TOOL_LLVM_AR_BUILD=False \
 -DLLVM_TOOL_LLVM_AS_BUILD=False \
 -DLLVM_TOOL_LLVM_AS_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_BCANALYZER_BUILD=False \
 -DLLVM_TOOL_LLVM_CAT_BUILD=False \
 -DLLVM_TOOL_LLVM_CFI_VERIFY_BUILD=False \
 -DLLVM_TOOL_LLVM_COV_BUILD=False \
 -DLLVM_TOOL_LLVM_CVTRES_BUILD=False \
 -DLLVM_TOOL_LLVM_C_TEST_BUILD=False \
 -DLLVM_TOOL_LLVM_DEMANGLE_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_DIFF_BUILD=False \
 -DLLVM_TOOL_LLVM_DIS_BUILD=False \
 -DLLVM_TOOL_LLVM_DWARFDUMP_BUILD=False \
 -DLLVM_TOOL_LLVM_DWP_BUILD=False \
 -DLLVM_TOOL_LLVM_EXEGESIS_BUILD=False \
 -DLLVM_TOOL_LLVM_EXTRACT_BUILD=False \
 -DLLVM_TOOL_LLVM_GO_BUILD=False \
 -DLLVM_TOOL_LLVM_ISEL_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_JITLISTENER_BUILD=False \
 -DLLVM_TOOL_LLVM_LINK_BUILD=False \
 -DLLVM_TOOL_LLVM_LTO2_BUILD=False \
 -DLLVM_TOOL_LLVM_LTO_BUILD=False \
 -DLLVM_TOOL_LLVM_MCA_BUILD=False \
 -DLLVM_TOOL_LLVM_MC_ASSEMBLE_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_MC_BUILD=False \
 -DLLVM_TOOL_LLVM_MC_DISASSEMBLE_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_MODEXTRACT_BUILD=False \
 -DLLVM_TOOL_LLVM_MT_BUILD=False \
 -DLLVM_TOOL_LLVM_NM_BUILD=False \
 -DLLVM_TOOL_LLVM_OBJCOPY_BUILD=False \
 -DLLVM_TOOL_LLVM_OBJDUMP_BUILD=False \
 -DLLVM_TOOL_LLVM_OPT_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_OPT_REPORT_BUILD=False \
 -DLLVM_TOOL_LLVM_PDBUTIL_BUILD=False \
 -DLLVM_TOOL_LLVM_PROFDATA_BUILD=False \
 -DLLVM_TOOL_LLVM_RC_BUILD=False \
 -DLLVM_TOOL_LLVM_READOBJ_BUILD=False \
 -DLLVM_TOOL_LLVM_RTDYLD_BUILD=False \
 -DLLVM_TOOL_LLVM_SHLIB_BUILD=False \
 -DLLVM_TOOL_LLVM_SIZE_BUILD=False \
 -DLLVM_TOOL_LLVM_SPECIAL_CASE_LIST_FUZZER_BUILD=False \
 -DLLVM_TOOL_LLVM_SPLIT_BUILD=False \
 -DLLVM_TOOL_LLVM_STRESS_BUILD=False \
 -DLLVM_TOOL_LLVM_STRINGS_BUILD=False \
 -DLLVM_TOOL_LLVM_SYMBOLIZER_BUILD=False \
 -DLLVM_TOOL_LLVM_UNDNAME_BUILD=False \
 -DLLVM_TOOL_LLVM_XRAY_BUILD=False \
 -DLLVM_TOOL_LTO_BUILD=False \
 -DLLVM_TOOL_OBJ2YAML_BUILD=False \
 -DLLVM_TOOL_OPT_BUILD=True \
 -DLLVM_TOOL_OPT_VIEWER_BUILD=False \
 -DLLVM_TOOL_SANCOV_BUILD=False \
 -DLLVM_TOOL_SANSTATS_BUILD=False \
 -DLLVM_TOOL_VERIFY_USELISTORDER_BUILD=False \
 -DLLVM_TOOL_XCODE_TOOLCHAIN_BUILD=False \
 -DLLVM_TOOL_YAML2OBJ_BUILD=False \
 -DLLVM_USE_FOLDERS=False \
 -G "Ninja" \
 ../llvm
cmake --build .
```

## Acknowledgements

This material is based upon work supported by the United States Air Force and
Defense Advanced Research Project Agency (DARPA) under
Contract No. FA8750-19-C-0004. Any opinions, findings and conclusions or
recommendations expressed in this material are those of the author(s) and do
not necessarily reflect the views of the United States Air Force or DARPA.
Approved for Public Release, Distribution Unlimited.
