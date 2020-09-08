
# Vulkan

- Specify intent (more verbose)

#### Steps to draw a triangle

1. Instance and physical device selection

VkInstance: set up Vulkan API

2. Logical device and queue families

VkDevice: which physical device feature to use.

Commands submitted to VkQueue.

Queues for graphics, compute and memory-transactions.

3. Window surface and swap chain

Must create a window to present rendered images to.

Window surface: VkSurfaceKHR, Swap chain: VkSwapchainKHR.

(KHR->Vulkan extension)

Vulkan API platform agnostic, need Window System Interface.

Swap chain: render targets. Ensure image we are rendering to is different from
the one on the screen. Enusure only complete images are shown.

4. Image views and framebuffers

VkImageView & VkFramebuffer.

Image view: Specific part of image to be used.

Framebuffer: image views to be used for color, depth and stencil targets.

5. Render passes

Describe type of images used during rendering operations, how they will be used,
how their contents should be treated.

6. Graphics pipeline

VkPipeline: configurable state of graphics card.

Almost all config must be set in advance.

Like ahead-of-time compilation. More optimization opportunities and runtime perf is more predictable.

7. Command pools and command buffers

Operations need to be recorded into a VkCommandBuffer before they can be submitted.

To draw simple triangle:

1. Begin render pass
2. Bind graphics pipeline
3. Draw 3 vertices
4. End render pass

8. Main loop

Acquire image from the swap chain with vkAcquireNextImageKHR.
Select appropriate command buffer for the image and execute it with vkQueueSubmit.
Return image to the swap chain for presentation to screen with vkQueuePresentKHR.

#### API concepts

Coding conventions:
vk-prefix: functions
Vk-prefix: enumerations/structs

Validation layers:
Limited error checking and debugging capabilities by default (want high perf)
VLs: pieces of code that can be inserted between API and graphics driver.
