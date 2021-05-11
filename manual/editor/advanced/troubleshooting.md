
# Troubleshooting

This page contains listings of commonplace (and less commonplace) issues related to the Flax Editor and Engine, and their respective possible solutions.


## Intel iGPUs and DirectX Error `E_INVALIDARG`


### Symptoms:
When attempting to build scene data, the Flax Editor crashes and displays an error message:

![Crash Error Message](https://i.imgur.com/L1JnGYb.png)


### Causes:
This is caused by a broken SM5 shader implementation in certain Intel Chipsets.\
Essentially, the Intel graphics lies about supporting certain functionality, and then errors when DirectX calls those functions it lied about supporting. Thanks ~~Obama~~ *Intel*.


### Solutions & Workarounds
Depending on the age and model of your iGPU, it may be possible to bypass the issue by forcing Flax Editor to run in Vulkan or DirectX 10 mode using [command line parameters](https://docs.flaxengine.com/manual/editor/advanced/command-line-access.html).

> **Note:**\
> *Please keep in mind that the DirectX 10 backend isn't optimized,\
> and might occasionally not support a given feature.*

**Vulcan:**\
`FlaxEditor.exe -project "C:\Users\<Username>\Documents\Flax Projects\MyProject" -vulkan`

**DirectX 10:**\
`FlaxEditor.exe -project "C:\Users\<Username>\Documents\Flax Projects\MyProject" -d3d10`


> **Note:**\
> If Vulkan is not supported by your hardware, Flax will transparently fall back onto DirectX 11 and you will experience the exact same issue. This can be confirmed by searching the log file for
> `VK_ERROR_INITIALIZATION_FAILED`.
> 
> If this happens, please try DirectX 10 instead.

