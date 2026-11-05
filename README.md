# nodos binary tools
These binaries are required for nodos, for the first time build execution, or some binaries which are not compiled from source code.

## Windows tools and the UTF-8 code page
`glslc.exe` and `spirv-opt.exe` are the Vulkan SDK's, with `<activeCodePage>UTF-8</activeCodePage>` added to their embedded manifest so that their paths are not limited to the system code page. Taking a new version from the SDK needs the same two steps, which also drop LunarG's signature, since it does not cover the changed file:

    signtool remove /s glslc.exe
    mt -manifest ../utf8.manifest -outputresource:glslc.exe;#1
