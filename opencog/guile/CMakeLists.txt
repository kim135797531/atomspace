INCLUDE_DIRECTORIES(
	${GUILE_INCLUDE_DIR}
)

ADD_LIBRARY (smob SHARED
	SchemeEval.cc
	SchemeExec.cc
	SchemePrimitive.cc
	SchemeSmob.cc
	SchemeSmobAtom.cc
	SchemeSmobAS.cc
	SchemeSmobAV.cc
	SchemeSmobGC.cc
	SchemeSmobNew.cc
	SchemeSmobTV.cc
	SchemeSmobAF.cc
	load-file
)

TARGET_LINK_LIBRARIES(smob
	atomspace
	execution
	${COGUTIL_LIBRARY}
	${GUILE_LIBRARIES}
)

ADD_EXECUTABLE(PrimitiveExample
	PrimitiveExample.cc
)
TARGET_LINK_LIBRARIES(PrimitiveExample
	smob
	atomspace
)

INSTALL (TARGETS smob DESTINATION "lib${LIB_DIR_SUFFIX}/opencog")

INSTALL (FILES
	SchemeEval.h
	SchemePrimitive.h
	SchemeSmob.h
	load-file.h
	DESTINATION "include/${PROJECT_NAME}/guile"
)
