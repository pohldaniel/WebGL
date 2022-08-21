# WebGL
This repository contains some researches and examples I have made during diving into Webassembly.

The Project 01Triangle-emscripten uses the Emscripten sdk from https://emscripten.org for compilling the content and Python for setting up a small HTTP-Server wich can serve the results. I managed to translate the example WebGL from https://github.com/schellingb/ClangWasm back to emscripten but just using custom WebGL without GLFW or SDL. Unfortunataly I wasn't able to figure out how to use Clang on windows for compile the .wasm files.

em++ librarytest.cc --js-library library.js -s "EXPORTED_FUNCTIONS=['_WAFNDraw','_main']" -o index.js

python wasm_server.py

clang -cc1 -triple wasm32-unknown-emscripten -emit-obj -D EMSCRIPTEN -I include -o librarytest.o -x c++ librarytest.cc

wasm-ld -o index.wasm librarytest.o -L lib\libgl.a lib\libc.a lib\libcompiler_rt.a lib\libc_rt_wasm.a --allow-undefined --export WAFNDraw --export WAJS_SetupCanvas --export main --export emscripten_stack_get_end --export emscripten_stack_get_free --export emscripten_stack_init --export stackSave --export stackRestore --export stackAlloc --export __wasm_call_ctors --export fflush --export __errno_location --export-table -z stack-size=5242880 --initial-memory=16777216 --no-entry --max-memory=16777216 --global-base=1024
