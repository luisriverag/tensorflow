load("//tensorflow:tensorflow.bzl", "tf_cc_test")
load("//tensorflow:tensorflow.default.bzl", "filegroup")
load("//tensorflow/compiler/mlir:glob_lit_test.bzl", "glob_lit_tests")

package(
    # copybara:uncomment default_applicable_licenses = ["//tensorflow:license"],
    licenses = ["notice"],
)

glob_lit_tests(
    name = "all_tests",
    data = [":test_utilities"],
    # TODO: b/288344501 - Enable OSS tests again when stable-quant-opt works well.
    default_tags = [
        "no_oss",
        "no_pip",
    ],
    driver = "//tensorflow/compiler/mlir/quantization/stablehlo:run_lit.sh",
    size_override = {
    },
    tags_override = {
    },
    test_file_exts = ["mlir"],
)

# Bundle together all of the test utilities that are used by tests.
filegroup(
    name = "test_utilities",
    testonly = True,
    data = [
        "//tensorflow/compiler/mlir/quantization/stablehlo:stablehlo-quant-opt",
        "@llvm-project//llvm:FileCheck",
        "@llvm-project//llvm:not",
        "@llvm-project//mlir:run_lit.sh",
    ],
)

tf_cc_test(
    name = "fill_quantization_options_test",
    srcs = ["fill_quantization_options_test.cc"],
    deps = [
        "//tensorflow/compiler/mlir/quantization/stablehlo:fill_quantization_options",
        "//tensorflow/compiler/mlir/quantization/stablehlo:quantization_options_proto_cc",
        "@com_google_googletest//:gtest_main",
        "@llvm-project//llvm:Support",
        "@local_tsl//tsl/platform:protobuf",
    ],
)
