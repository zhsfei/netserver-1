## Process this file with automake to produce Makefile.in

if HAVE_ZLIB
GZCHECKPROGRAMS = zcgzip zcgunzip
GZHEADERS = google/protobuf/io/gzip_stream.h
GZTESTS = google/protobuf/io/gzip_stream_unittest.sh
else
GZCHECKPROGRAMS =
GZHEADERS =
GZTESTS =
endif

noinst_LIBRARIES =  libprotobuf.a libprotoc.a libprotobuf_lite.a

NO_OPT_CXXFLAGS = $(PTHREAD_CFLAGS) -Wall -Wwrite-strings -Woverloaded-virtual -Wno-sign-compare

AM_CXXFLAGS = $(NO_OPT_CXXFLAGS) $(PROTOBUF_OPT_FLAG)

AM_LDFLAGS = $(PTHREAD_CFLAGS)

# If I say "dist_include_DATA", automake complains that $(includedir) is not
# a "legitimate" directory for DATA.  Screw you, automake.
protodir = $(includedir)
nobase_dist_proto_DATA = google/protobuf/descriptor.proto 

# Not sure why these don't get cleaned automatically.
clean-local:
	rm -f *.loT

CLEANFILES = $(protoc_outputs) unittest_proto_middleman \
             testzip.jar testzip.list testzip.proto testzip.zip

MAINTAINERCLEANFILES =   \
  Makefile.in

nobase_include_HEADERS =                                       \
  google/protobuf/stubs/common.h                               \
  google/protobuf/stubs/once.h                                 \
  google/protobuf/descriptor.h                                 \
  google/protobuf/descriptor.pb.h                              \
  google/protobuf/descriptor_database.h                        \
  google/protobuf/dynamic_message.h                            \
  google/protobuf/extension_set.h                              \
  google/protobuf/generated_message_util.h                     \
  google/protobuf/generated_message_reflection.h               \
  google/protobuf/message.h                                    \
  google/protobuf/message_lite.h                               \
  google/protobuf/reflection_ops.h                             \
  google/protobuf/repeated_field.h                             \
  google/protobuf/service.h                                    \
  google/protobuf/text_format.h                                \
  google/protobuf/unknown_field_set.h                          \
  google/protobuf/wire_format.h                                \
  google/protobuf/wire_format_lite.h                           \
  google/protobuf/wire_format_lite_inl.h                       \
  google/protobuf/io/coded_stream.h                            \
  $(GZHEADERS)                                                 \
  google/protobuf/io/printer.h                                 \
  google/protobuf/io/tokenizer.h                               \
  google/protobuf/io/zero_copy_stream.h                        \
  google/protobuf/io/zero_copy_stream_impl.h                   \
  google/protobuf/io/zero_copy_stream_impl_lite.h              \
  google/protobuf/compiler/code_generator.h                    \
  google/protobuf/compiler/command_line_interface.h            \
  google/protobuf/compiler/importer.h                          \
  google/protobuf/compiler/parser.h                            \
  google/protobuf/compiler/cpp/cpp_generator.h                 

#libprotobuf_lite_a_LIBADD = $(PTHREAD_LIBS)
#libprotobuf_lite_a_LDFLAGS = -export-dynamic -no-undefined
libprotobuf_lite_a_SOURCES =                                  \
  google/protobuf/stubs/common.cc                              \
  google/protobuf/stubs/once.cc                                \
  google/protobuf/stubs/hash.cc                                \
  google/protobuf/stubs/hash.h                                 \
  google/protobuf/stubs/map-util.h                             \
  google/protobuf/stubs/stl_util-inl.h                         \
  google/protobuf/extension_set.cc                             \
  google/protobuf/generated_message_util.cc                    \
  google/protobuf/message_lite.cc                              \
  google/protobuf/repeated_field.cc                            \
  google/protobuf/wire_format_lite.cc                          \
  google/protobuf/io/coded_stream.cc                           \
  google/protobuf/io/coded_stream_inl.h                        \
  google/protobuf/io/zero_copy_stream.cc                       \
  google/protobuf/io/zero_copy_stream_impl_lite.cc

#libprotobuf_a_LIBADD = $(PTHREAD_LIBS)
#libprotobuf_a_LDFLAGS = -export-dynamic -no-undefined
libprotobuf_a_SOURCES =                                       \
  $(libprotobuf_lite_a_SOURCES)                               \
  google/protobuf/stubs/strutil.cc                             \
  google/protobuf/stubs/strutil.h                              \
  google/protobuf/stubs/substitute.cc                          \
  google/protobuf/stubs/substitute.h                           \
  google/protobuf/stubs/structurally_valid.cc                  \
  google/protobuf/descriptor.cc                                \
  google/protobuf/descriptor.pb.cc                             \
  google/protobuf/descriptor_database.cc                       \
  google/protobuf/dynamic_message.cc                           \
  google/protobuf/extension_set_heavy.cc                       \
  google/protobuf/generated_message_reflection.cc              \
  google/protobuf/message.cc                                   \
  google/protobuf/reflection_ops.cc                            \
  google/protobuf/service.cc                                   \
  google/protobuf/text_format.cc                               \
  google/protobuf/unknown_field_set.cc                         \
  google/protobuf/wire_format.cc                               \
  google/protobuf/io/gzip_stream.cc                            \
  google/protobuf/io/printer.cc                                \
  google/protobuf/io/tokenizer.cc                              \
  google/protobuf/io/zero_copy_stream_impl.cc                  \
  google/protobuf/compiler/importer.cc                         \
  google/protobuf/compiler/parser.cc

#libprotoc_a_LIBADD = $(PTHREAD_LIBS) libprotobuf.a
#libprotoc_a_LDFLAGS = -export-dynamic -no-undefined
libprotoc_a_SOURCES = $(libprotobuf_a_SOURCES)         \
  google/protobuf/compiler/code_generator.cc                   \
  google/protobuf/compiler/command_line_interface.cc           \
  google/protobuf/compiler/cpp/cpp_enum.cc                     \
  google/protobuf/compiler/cpp/cpp_enum.h                      \
  google/protobuf/compiler/cpp/cpp_enum_field.cc               \
  google/protobuf/compiler/cpp/cpp_enum_field.h                \
  google/protobuf/compiler/cpp/cpp_extension.cc                \
  google/protobuf/compiler/cpp/cpp_extension.h                 \
  google/protobuf/compiler/cpp/cpp_field.cc                    \
  google/protobuf/compiler/cpp/cpp_field.h                     \
  google/protobuf/compiler/cpp/cpp_file.cc                     \
  google/protobuf/compiler/cpp/cpp_file.h                      \
  google/protobuf/compiler/cpp/cpp_generator.cc                \
  google/protobuf/compiler/cpp/cpp_helpers.cc                  \
  google/protobuf/compiler/cpp/cpp_helpers.h                   \
  google/protobuf/compiler/cpp/cpp_message.cc                  \
  google/protobuf/compiler/cpp/cpp_message.h                   \
  google/protobuf/compiler/cpp/cpp_message_field.cc            \
  google/protobuf/compiler/cpp/cpp_message_field.h             \
  google/protobuf/compiler/cpp/cpp_primitive_field.cc          \
  google/protobuf/compiler/cpp/cpp_primitive_field.h           \
  google/protobuf/compiler/cpp/cpp_service.cc                  \
  google/protobuf/compiler/cpp/cpp_service.h                   \
  google/protobuf/compiler/cpp/cpp_string_field.cc             \
  google/protobuf/compiler/cpp/cpp_string_field.h              

bin_PROGRAMS = protoc
protoc_LDADD = $(PTHREAD_LIBS)$(noinst_LIBRARIES) libprotobuf.a libprotoc.a
protoc_SOURCES = google/protobuf/compiler/main.cc

# Tests ==============================================================

protoc_inputs =                                                \
  google/protobuf/unittest.proto                               \
  google/protobuf/unittest_empty.proto                         \
  google/protobuf/unittest_import.proto                        \
  google/protobuf/unittest_mset.proto                          \
  google/protobuf/unittest_optimize_for.proto                  \
  google/protobuf/unittest_embed_optimize_for.proto            \
  google/protobuf/unittest_custom_options.proto                \
  google/protobuf/unittest_lite.proto                          \
  google/protobuf/unittest_import_lite.proto                   \
  google/protobuf/unittest_lite_imports_nonlite.proto          \
  google/protobuf/compiler/cpp/cpp_test_bad_identifiers.proto

EXTRA_DIST =                                                   \
  $(protoc_inputs)                                             \
  google/protobuf/io/gzip_stream.h                             \
  google/protobuf/io/gzip_stream_unittest.sh                   \
  google/protobuf/testdata/golden_message                      \
  google/protobuf/testdata/golden_packed_fields_message        \
  google/protobuf/testdata/text_format_unittest_data.txt       \
  google/protobuf/testdata/text_format_unittest_extensions_data.txt  \
  google/protobuf/package_info.h                               \
  google/protobuf/io/package_info.h                            \
  google/protobuf/compiler/package_info.h                      \
  google/protobuf/unittest_enormous_descriptor.proto

protoc_lite_outputs =                                          \
  google/protobuf/unittest_lite.pb.cc                          \
  google/protobuf/unittest_lite.pb.h                           \
  google/protobuf/unittest_import_lite.pb.cc                   \
  google/protobuf/unittest_import_lite.pb.h

protoc_outputs =                                               \
  $(protoc_lite_outputs)                                       \
  google/protobuf/unittest.pb.cc                               \
  google/protobuf/unittest.pb.h                                \
  google/protobuf/unittest_empty.pb.cc                         \
  google/protobuf/unittest_empty.pb.h                          \
  google/protobuf/unittest_import.pb.cc                        \
  google/protobuf/unittest_import.pb.h                         \
  google/protobuf/unittest_mset.pb.cc                          \
  google/protobuf/unittest_mset.pb.h                           \
  google/protobuf/unittest_optimize_for.pb.cc                  \
  google/protobuf/unittest_optimize_for.pb.h                   \
  google/protobuf/unittest_embed_optimize_for.pb.cc            \
  google/protobuf/unittest_embed_optimize_for.pb.h             \
  google/protobuf/unittest_custom_options.pb.cc                \
  google/protobuf/unittest_custom_options.pb.h                 \
  google/protobuf/unittest_lite_imports_nonlite.pb.cc          \
  google/protobuf/unittest_lite_imports_nonlite.pb.h           \
  google/protobuf/unittest_no_generic_services.pb.cc           \
  google/protobuf/unittest_no_generic_services.pb.h            \
  google/protobuf/compiler/cpp/cpp_test_bad_identifiers.pb.cc  \
  google/protobuf/compiler/cpp/cpp_test_bad_identifiers.pb.h

BUILT_SOURCES = $(protoc_outputs)

if USE_EXTERNAL_PROTOC

unittest_proto_middleman: $(protoc_inputs)
	$(PROTOC) -I$(srcdir) --cpp_out=. $^
	touch unittest_proto_middleman

else

# This rule is a little weird.  The first prereq is the protoc executable
# and the rest are its inputs.  Therefore, $^ -- which expands to the
# list of prereqs -- is actually a valid command.  We have to place "./" in
# front of it in case protoc is in the current directory.  protoc allows
# flags to appear after input file names, so we happily stick the flags on
# the end.
#
# For reference, if we didn't have to worry about VPATH (i.e., building from
# a directory other than the package root), we could have just written this:
#   ./protoc$(EXEEXT) -I$(srcdir) --cpp_out=. $(protoc_inputs)
unittest_proto_middleman: protoc$(EXEEXT) $(protoc_inputs)
	./$^ -I$(srcdir) --cpp_out=.
	touch unittest_proto_middleman

endif

$(protoc_outputs): unittest_proto_middleman

check_PROGRAMS = protoc $(GZCHECKPROGRAMS)

if HAVE_ZLIB
zcgzip_LDADD = $(PTHREAD_LIBS) libprotobuf.a
zcgzip_SOURCES = google/protobuf/testing/zcgzip.cc

zcgunzip_LDADD = $(PTHREAD_LIBS) libprotobuf.a
zcgunzip_SOURCES = google/protobuf/testing/zcgunzip.cc
endif

TESTS =  google/protobuf/compiler/zip_output_unittest.sh $(GZTESTS)
