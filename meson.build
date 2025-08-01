project('mupen64plus-video-parallel', ['c', 'cpp'],
  version : '0.1'
)

prefix = get_option('prefix')
libdir = prefix / get_option('libdir')
plugins_dir = prefix / libdir / 'mupen64plus'

add_project_arguments([
  '-DM64P_PLUGIN_API',
  '-Wno-missing-field-initializers',
  '-Wno-unused-variable',
  '-Wno-sign-compare',
], language: ['c', 'cpp'])

parallel_include_dirs = include_directories([
  'parallel-rdp',
  'vulkan',
  'volk',
  'util',
  '.'
])

parallel_rdp_source = [
  'parallel-rdp/command_ring.cpp',
  'parallel-rdp/rdp_device.cpp',
  'parallel-rdp/rdp_dump_write.cpp',
  'parallel-rdp/rdp_renderer.cpp',
  'parallel-rdp/video_interface.cpp',

  'util/aligned_alloc.cpp',
  'util/arena_allocator.cpp',
  'util/environment.cpp',
  'util/logging.cpp',
  'util/thread_id.cpp',
  'util/thread_name.cpp',
  'util/timeline_trace_file.cpp',
  'util/timer.cpp',

  'volk/volk.c',

  'vulkan/buffer.cpp',
  'vulkan/buffer_pool.cpp',
  'vulkan/command_buffer.cpp',
  'vulkan/command_pool.cpp',
  'vulkan/context.cpp',
  'vulkan/cookie.cpp',
  'vulkan/descriptor_set.cpp',
  'vulkan/device.cpp',
  'vulkan/event_manager.cpp',
  'vulkan/fence.cpp',
  'vulkan/fence_manager.cpp',
  'vulkan/image.cpp',
  'vulkan/indirect_layout.cpp',
  'vulkan/memory_allocator.cpp',
  'vulkan/pipeline_event.cpp',
  'vulkan/query_pool.cpp',
  'vulkan/render_pass.cpp',
  'vulkan/sampler.cpp',
  'vulkan/semaphore.cpp',
  'vulkan/semaphore_manager.cpp',
  'vulkan/shader.cpp',
  'vulkan/texture/texture_format.cpp',
  'vulkan/wsi.cpp',

  'gfx_m64p.cpp',
  'glguts.cpp',
  'parallel_imp.cpp',
]

parallel_rdp_deps = [
  dependency('gl'),
  dependency('vulkan'),
]

shared_library('mupen64plus-video-parallel',
  parallel_rdp_source,
  dependencies: parallel_rdp_deps,
  include_directories: parallel_include_dirs,
  name_prefix : '',
  install: true,
  install_dir: plugins_dir,
)
