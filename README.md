## File structure
1. The `patchs` directory is the patch of the chromium source code used in this project

## Build
1. Install depot_tools and set environment
2. Run `cipd ensure -root . -ensure-file gn-win.ensure` or `cipd ensure -root . -ensure-file gn-linux.ensure` to download gn.
3. If you want use chromium default toolchain Run `python3 tools/clang/scripts/update.py`
4. set `CHROMIUM_BUILDTOOLS_PATH` environment to `buildtools` real path
5. Run `gn gen llvmout/ReleaseMD --args="use_custom_libcxx=false clang_use_chrome_plugins=false clang_base_path=\"to sume llvm path\" forbid_non_component_debug_builds=false treat_warnings_as_errors=false is_component_build=false is_debug=false symbol_level=0 use_allocator_shim=false use_allocator=\"none\""` to build static library. If you want build with default chromium toolchain remove `clang_use_chrome_plugins` and `clang_base_path` gn args. If you want build shared version change `is_component_build` to `true` 