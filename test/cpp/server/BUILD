# Copyright 2017 gRPC authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("//bazel:grpc_build_system.bzl", "grpc_cc_test", "grpc_package")

licenses(["notice"])

grpc_package(name = "test/cpp/server")

grpc_cc_test(
    name = "server_builder_test",
    srcs = ["server_builder_test.cc"],
    external_deps = [
        "gtest",
    ],
    tags = [
        "no_windows",
        # TODO(b/399766758): Remove this tag once the test is fixed.
        "grpc:fails-internally",
    ],
    deps = [
        "//:grpc++_unsecure",
        "//src/proto/grpc/testing:echo_cc_grpc",
        "//test/core/event_engine:event_engine_test_utils",
        "//test/core/test_util:grpc_test_util_base",
        "//test/core/test_util:grpc_test_util_unsecure",
    ],
)

grpc_cc_test(
    name = "server_builder_with_socket_mutator_test",
    srcs = ["server_builder_with_socket_mutator_test.cc"],
    external_deps = [
        "gtest",
    ],
    tags = [
        "no_windows",
        # TODO(b/399766758): Remove this tag once the test is fixed.
        "grpc:fails-internally",
    ],
    deps = [
        "//:grpc++_unsecure",
        "//src/proto/grpc/testing:echo_cc_grpc",
        "//test/core/test_util:grpc_test_util_base",
        "//test/core/test_util:grpc_test_util_unsecure",
    ],
)

grpc_cc_test(
    name = "server_request_call_test",
    srcs = ["server_request_call_test.cc"],
    external_deps = [
        "gtest",
    ],
    tags = ["no_windows"],
    deps = [
        "//:grpc++",
        "//src/proto/grpc/testing:echo_cc_grpc",
        "//test/core/test_util:grpc_test_util",
        "//test/core/test_util:grpc_test_util_base",
    ],
)

grpc_cc_test(
    name = "credentials_test",
    srcs = ["credentials_test.cc"],
    data = [
        "//src/core/tsi/test_creds:ca.pem",
        "//src/core/tsi/test_creds:malformed-cert.pem",
        "//src/core/tsi/test_creds:malformed-key.pem",
        "//src/core/tsi/test_creds:server1.key",
        "//src/core/tsi/test_creds:server1.pem",
    ],
    external_deps = [
        "absl/log:check",
        "gtest",
    ],
    deps = [
        "//:gpr",
        "//:grpc",
        "//:grpc++",
        "//:grpc++_base",
        "//test/core/test_util:grpc_test_util",
        "//test/cpp/util:tls_test_utils",
    ],
)

grpc_cc_test(
    name = "authorization_policy_provider_test",
    srcs = ["authorization_policy_provider_test.cc"],
    data = [
        "//test/core/security/authorization/test_policies:invalid_policy.json",
        "//test/core/security/authorization/test_policies:valid_policy_1.json",
        "//test/core/security/authorization/test_policies:valid_policy_2.json",
    ],
    external_deps = [
        "gtest",
    ],
    # Test seems to be failing on iOS, but shouldn't be needed there anyway,
    # since we don't support servers on iOS.
    tags = ["no_test_ios"],
    deps = [
        "//:gpr",
        "//:grpc",
        "//:grpc++",
        "//:grpc++_authorization_provider",
        "//test/core/test_util:grpc_test_util",
    ],
)

grpc_cc_test(
    name = "orca_service_test",
    srcs = ["orca_service_test.cc"],
    external_deps = [
        "absl/time",
        "gtest",
    ],
    deps = [
        "//:grpc++",
        "//:grpcpp_backend_metric_recorder",
        "//:grpcpp_call_metric_recorder",
        "//:grpcpp_orca_service",
        "//src/core:notification",
        "//test/core/test_util:grpc_test_util",
        "//test/cpp/util:test_util",
    ],
)
