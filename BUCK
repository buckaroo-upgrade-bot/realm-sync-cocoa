load('//:utils.bzl', 'extract', 'extractFolder')

version = '3.13.3'

http_archive(
  name = 'realm-sync-cocoa-archive',
  out = 'out',
  urls = [
    'https://static.realm.io/downloads/sync/realm-sync-cocoa-' + version + '.tar.xz',
  ],
  sha256 = '14acd38d0f3875392aa53db5adcaa33fb65bb79feb2af1af26e8c2704db96838',
)

prebuilt_cxx_library(
  name = 'realm', 
  header_dirs = [
    extractFolder(':realm-sync-cocoa-archive', 'core/include'),
  ],
  preferred_linkage = 'static', 
  platform_shared_lib = [
    ('macos.*', extract(':realm-sync-cocoa-archive', 'core/librealm-macosx.a')),
    ('iphone.*', extract(':realm-sync-cocoa-archive', 'core/librealm-ios.a')),
  ], 
  visibility = [
    'PUBLIC',
  ],
)

prebuilt_cxx_library(
  name = 'realm-parser', 
  preferred_linkage = 'static', 
  platform_shared_lib = [
    ('macos.*', extract(':realm-sync-cocoa-archive', 'core/librealm-parser-macosx.a')),
    ('iphone.*', extract(':realm-sync-cocoa-archive', 'core/librealm-parser-ios.a')),
  ], 
  deps = [
    ':realm',
  ],
  visibility = [
    'PUBLIC',
  ],
)
