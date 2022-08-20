# WebGL
This repository contains some researches and examples I have made during diving into Webassembly.

The Project 01Triangle-emscripten uses the Emscripten sdk from https://emscripten.org for compilling the content and Python for setting up a small HTTP-Server wich can serve the results. I managed to translate the example WebGL from https://github.com/schellingb/ClangWasm back to emscripten but just using custom WebGL without GLFW or SDL. Unfortunataly I wasn't able to figure out how to use Clang on windows for compile the .wasm files.

em++ librarytest.cc --js-library library.js -s "EXPORTED_FUNCTIONS=['_WAFNDraw','_main']" -o index.js

python wasm_server.py
