load("@fastly//util.bzl", "splat_headers")

cxx_library(
  name = "theft",
  header_namespace = "",
  exported_headers = splat_headers(["inc/*.h"]),
  headers = splat_headers(["src/*.h"]),
  srcs = glob(["src/*.c"]),
  visibility = ["PUBLIC"],
)

prebuilt_cxx_library(
  name = "internal-headers",
  visibility = ["//test/..."],
  header_only = True,
  exported_headers = splat_headers(["src/*.h"]),
  header_namespace = "",
)

# the makefile says this is needed for theft_bloom and theft_shrink, but it's
# not actually included in either
genrule(
  name = "bits_lut.h",
  srcs = ["scripts/mk_bits_lut"],
  out = "bits_lut.h",
  cmd = """
    ${SRCDIR}/scripts/mk_bits_lut > ${OUT}
  """
)
