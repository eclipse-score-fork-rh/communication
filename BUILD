# *******************************************************************************
# Copyright (c) 2024 Contributors to the Eclipse Foundation
#
# See the NOTICE file(s) distributed with this work for additional
# information regarding copyright ownership.
#
# This program and the accompanying materials are made available under the
# terms of the Apache License Version 2.0 which is available at
# https://www.apache.org/licenses/LICENSE-2.0
#
# SPDX-License-Identifier: Apache-2.0
# *******************************************************************************

load("@aspect_rules_lint//format:defs.bzl", "format_multirun", "format_test")
load("@rules_rpm//rpm:defs.bzl", "rpm_package")

exports_files([
    "wait_free_stack_fix.patch",
])

format_multirun(
    name = "format",
    cc = "@clang_format//:executable",
    starlark = "@buildifier_prebuilt//:buildifier",
)

format_test(
    name = "format_test",
    cc = "@clang_format//:executable",
    no_sandbox = True,
    starlark = "@buildifier_prebuilt//:buildifier",
    tags = ["manual"],
    workspace = "//:LICENSE",
)

rpm_package(
    name = "lola-devel",
    libraries = [
        "//score/mw/com:com",
        "//score/mw/com:config_schema",
    ],
    binaries = [
        "//score/mw/com/example/ipc_bridge:ipc_bridge_cpp",
        "//score/mw/com/example/ipc_bridge:ipc_bridge_rs",
    ],
    data = [
        "//score/mw/com/example/ipc_bridge:etc/mw_com_config.json",
    ],
    config_dir = "/etc/lola",
    data_dir = "/usr/share/lola/examples",
    version = "1.0.0",
    summary = "LOLA Demo",
    description = "LOLA middleware communication libraries for development including core communication, configuration components, and example client/server binaries for testing",
)
