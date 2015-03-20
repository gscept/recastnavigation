CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

PROJECT(RecastNavigation)
#SET(RECAST_VERSION r129)



IF(MSVC)
	OPTION(USE_MSVC_FAST_FLOATINGPOINT "Use MSVC /fp:fast option" ON)
	IF(USE_MSVC_FAST_FLOATINGPOINT)
		ADD_DEFINITIONS(/fp:fast)
	ENDIF(USE_MSVC_FAST_FLOATINGPOINT)
	ADD_DEFINITIONS(/D _CRT_SECURE_NO_WARNINGS)
ENDIF(MSVC)

INCLUDE_DIRECTORIES( 
	../Detour/Include
	../Recast/Include
	../DetourTileCache/Include
	../DebugUtils/Include
	../DetourCrowd/Include
)


SET(debugutils_SRCS 
	../DebugUtils/Source/DebugDraw.cpp
	../DebugUtils/Source/DetourDebugDraw.cpp
	../DebugUtils/Source/RecastDebugDraw.cpp
	../DebugUtils/Source/RecastDump.cpp
)

SET(debugutils_HDRS
	../DebugUtils/Include/DebugDraw.h
	../DebugUtils/Include/DetourDebugDraw.h
	../DebugUtils/Include/RecastDebugDraw.h
	../DebugUtils/Include/RecastDump.h
)

ADD_LIBRARY(DebugUtils ${debugutils_SRCS} ${debugutils_HDRS})


SET(detour_SRCS
	../Detour/Source/DetourAlloc.cpp
	../Detour/Source/DetourCommon.cpp
	../Detour/Source/DetourNavMesh.cpp
	../Detour/Source/DetourNavMeshBuilder.cpp
	../Detour/Source/DetourNavMeshQuery.cpp
	../Detour/Source/DetourNode.cpp
)

SET(detour_HDRS
	../Detour/Include/DetourAlloc.h
	../Detour/Include/DetourAssert.h
	../Detour/Include/DetourCommon.h
	../Detour/Include/DetourNavMesh.h
	../Detour/Include/DetourNavMeshBuilder.h
	../Detour/Include/DetourNavMeshQuery.h
	../Detour/Include/DetourNode.h
)

ADD_LIBRARY(Detour ${detour_SRCS} ${detour_HDRS})

SET(detourcrowd_SRCS
	../DetourCrowd/Source/DetourPathCorridor.cpp
	../DetourCrowd/Source/DetourLocalBoundary.cpp
	../DetourCrowd/Source/DetourObstacleAvoidance.cpp
	../DetourCrowd/Source/DetourPathQueue.cpp
	../DetourCrowd/Source/DetourCrowd.cpp
	../DetourCrowd/Source/DetourProximityGrid.cpp
)

SET(detourcrowd_HDRS
	../DetourCrowd/Include/DetourPathCorridor.h
	../DetourCrowd/Include/DetourCrowd.h
	../DetourCrowd/Include/DetourObstacleAvoidance.h
	../DetourCrowd/Include/DetourLocalBoundary.h
	../DetourCrowd/Include/DetourProximityGrid.h
	../DetourCrowd/Include/DetourPathQueue.h
)

ADD_LIBRARY(DetourCrowd ${detourcrowd_SRCS} ${detourcrowd_HDRS})


SET(detourtilecache_SRCS 
	../DetourTileCache/Source/DetourTileCache.cpp
	../DetourTileCache/Source/DetourTileCacheBuilder.cpp
)

SET(detourtilecache_HDRS
	../DetourTileCache/Include/DetourTileCache.h
	../DetourTileCache/Include/DetourTileCacheBuilder.h
)

ADD_LIBRARY(DetourTileCache ${detourtilecache_SRCS} ${detourtilecache_HDRS})

SET(recast_SRCS
	../Recast/Source/Recast.cpp
	../Recast/Source/RecastArea.cpp
	../Recast/Source/RecastAlloc.cpp
	../Recast/Source/RecastContour.cpp
	../Recast/Source/RecastFilter.cpp
	../Recast/Source/RecastLayers.cpp
	../Recast/Source/RecastMesh.cpp
	../Recast/Source/RecastMeshDetail.cpp
	../Recast/Source/RecastRasterization.cpp
	../Recast/Source/RecastRegion.cpp
)

SET(recast_HDRS
	../Recast/Include/Recast.h
	../Recast/Include/RecastAlloc.h
	../Recast/Include/RecastAssert.h
)

ADD_LIBRARY(Recast ${recast_SRCS} ${recast_HDRS})
