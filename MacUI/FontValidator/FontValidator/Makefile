# Copyright (c) Richard Fitzgerald

# All rights reserved.

# MIT License

# Permission is hereby granted, free of charge, to any person obtaining a copy of
# this software and associated documentation files (the ""Software""), to deal in
# the Software without restriction, including without limitation the rights to
# use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
# of the Software, and to permit persons to whom the Software is furnished to do
# so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

# Overview:

# Bundles the compiled FontVaildator.exe with the necessary Mono runtime to generate
# a self-contained executable that can be called by the Mac GUI app.
# the "touch" command ensures that the app gets codesigned if FontValidator is rebuilt.

# ROOT_DIR: root of main FontValidator repo
# BIN_DIR: location of compiled Mono executable
# OUT_DIR: destination directory
# MKB_OPTS: extra mkbundle command-line options
# MKB_LIBS: library options for mkbundle

ROOT_DIR=$(SRCROOT)/../..
BIN_DIR=$(ROOT_DIR)/bin
OUT_DIR=$(SRCROOT)/FontValidator
MKB_OPTS=-v --i18n all --simple
MKB_LIBS=--library libfreetype6.dylib,Darwin/libfreetype.6.dylib

$(OUT_DIR)/FontValidator: $(BIN_DIR)/FontValidator.exe Makefile
	cd $(BIN_DIR) && \
	mkbundle $(MKB_OPTS) -o $(OUT_DIR)/FontValidator FontValidator.exe $(MKB_LIBS)
	touch -cm $(OUT_DIR)/main.m

$(BIN_DIR)/FontValidator.exe:
	cd $(ROOT_DIR) && \
	$(MAKE)
