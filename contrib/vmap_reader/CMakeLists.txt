# Copyright (C) 2005-2009 MaNGOS project <http://getmangos.com/>
#
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without
# modifications, as long as this notice is preserved.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

cmake_minimum_required (VERSION 2.6)

project(VmapsReader)

ADD_DEFINITIONS(-DMMAP_GENERATOR -DNO_CORE_FUNCS -DDEBUG)

# zlib
ADD_DEFINITIONS( -DNO_vsnprintf )

ADD_DEFINITIONS("-ggdb")
ADD_DEFINITIONS("-O3")

include_directories(
    ${CMAKE_SOURCE_DIR}/src
    ${CMAKE_SOURCE_DIR}/src/shared
    ${CMAKE_SOURCE_DIR}/src/game
    ${CMAKE_SOURCE_DIR}/src/game/vmap
    ${CMAKE_SOURCE_DIR}/dep/include/g3dlite
    ${CMAKE_SOURCE_DIR}/src/framework
    ${CMAKE_SOURCE_DIR}/dep/ACE_wrappers
    ${CMAKE_SOURCE_DIR}/objdir/dep/ACE_wrappers
    ${CMAKE_SOURCE_DIR}/dep/recastnavigation/Detour/Include
    ${CMAKE_SOURCE_DIR}/dep/recastnavigation/Recast/Include
    ${CMAKE_SOURCE_DIR}/dep/src/zlib
)

add_library(zlib
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/adler32.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/compress.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/crc32.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/deflate.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/example.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/gzio.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/infback.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/inffast.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/inflate.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/inftrees.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/trees.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/uncompr.c
    ${CMAKE_SOURCE_DIR}/dep/src/zlib/zutil.c
)

add_library(g3dlite
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/AABox.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Any.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/AnyVal.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/AreaMemoryManager.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/BinaryFormat.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/BinaryInput.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/BinaryOutput.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Box.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Box2D.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/BumpMapPreprocess.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Capsule.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/CollisionDetection.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color1.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color1uint8.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color3.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color3uint8.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color4.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Color4uint8.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Cone.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/constants.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/ConvexPolyhedron.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/CoordinateFrame.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Crypto.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Crypto_md5.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Cylinder.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/debugAssert.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/fileutils.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/filter.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/format.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/g3dfnmatch.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/g3dmath.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/GCamera.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/GLight.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/GThread.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/GUniqueID.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Intersect.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/license.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Line.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/LineSegment.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Log.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Matrix.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Matrix3.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Matrix4.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/MemoryManager.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/MeshAlg.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/MeshAlgAdjacency.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/MeshAlgWeld.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/MeshBuilder.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/NetAddress.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/NetworkDevice.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/PhysicsFrame.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Plane.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/PrecomputedRandom.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/prompt.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Quat.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Random.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Ray.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Rect2D.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/ReferenceCount.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/RegistryUtil.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Sphere.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/SplineBase.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/stringutils.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/System.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/TextInput.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/TextOutput.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/ThreadSet.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Triangle.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/uint128.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/UprightFrame.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector2.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector2int16.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector3.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector3int16.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector3int32.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector4.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Vector4int8.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/Welder.cpp
    ${CMAKE_SOURCE_DIR}/dep/src/g3dlite/WinMain.cpp
)

target_link_libraries(g3dlite ${ZLIB_LIBRARIES})

add_library(vmap
    ${CMAKE_SOURCE_DIR}/src/game/vmap/BIH.cpp
    ${CMAKE_SOURCE_DIR}/src/game/vmap/VMapManager2.cpp
    ${CMAKE_SOURCE_DIR}/src/game/vmap/MapTree.cpp
    ${CMAKE_SOURCE_DIR}/src/game/vmap/TileAssembler.cpp
    ${CMAKE_SOURCE_DIR}/src/game/vmap/WorldModel.cpp
    ${CMAKE_SOURCE_DIR}/src/game/vmap/ModelInstance.cpp
)

target_link_libraries(vmap ${ZLIB_LIBRARIES} g3dlite)

set(SOURCES
    main.cpp
    VMapExtensions.cpp
)

add_executable(vmaps_reader ${SOURCES} )

target_link_libraries(vmaps_reader g3dlite vmap ${ZLIB_LIBRARIES})
