# WebGL

em++ librarytest.cc --js-library library.js -s "EXPORTED_FUNCTIONS=['_WAFNDraw','_main']" -o index.js

python wasm_server.py
