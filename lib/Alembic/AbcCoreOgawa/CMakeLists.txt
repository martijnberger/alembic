##-*****************************************************************************
##
## Copyright (c) 2013-2015,
##  Sony Pictures Imageworks Inc. and
##  Industrial Light & Magic, a division of Lucasfilm Entertainment Company Ltd.
##
## All rights reserved.
##
## Redistribution and use in source and binary forms, with or without
## modification, are permitted provided that the following conditions are
## met:
## *       Redistributions of source code must retain the above copyright
## notice, this list of conditions and the following disclaimer.
## *       Redistributions in binary form must reproduce the above
## copyright notice, this list of conditions and the following disclaimer
## in the documentation and/or other materials provided with the
## distribution.
## *       Neither the name of Industrial Light & Magic nor the names of
## its contributors may be used to endorse or promote products derived
## from this software without specific prior written permission.
##
## THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
## "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
## LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
## A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
## OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
## SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
## LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
## DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
## THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
## (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
## OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
##
##-*****************************************************************************

INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/lib)

SET(CXX_FILES
    AprImpl.cpp
    ApwImpl.cpp
    ArImpl.cpp
    AwImpl.cpp
    CprData.cpp
    CprImpl.cpp
    CpwData.cpp
    CpwImpl.cpp
    MetaDataMap.cpp
    OrData.cpp
    OrImpl.cpp
    OwData.cpp
    OwImpl.cpp
    ReadUtil.cpp
    ReadWrite.cpp
    SprImpl.cpp
    SpwImpl.cpp
    StreamManager.cpp
    WriteUtil.cpp
)

SET(H_FILES
    All.h
    AprImpl.h
    ApwImpl.h
    ArImpl.h
    AwImpl.h
    CprData.h
    CprImpl.h
    CpwData.h
    CpwImpl.h
    Foundation.h
    MetaDataMap.h
    OrData.h
    OrImpl.h
    OwData.h
    OwImpl.h
    ReadUtil.h
    ReadWrite.h
    SprImpl.h
    SpwImpl.h
    StreamManager.h
    WriteUtil.h
    WrittenSampleMap.h
)

SET(SOURCE_FILES ${CXX_FILES} ${H_FILES})

ADD_LIBRARY(AlembicAbcCoreOgawa OBJECT ${SOURCE_FILES})

IF(ALEMBIC_SHARED_LIBS)
  SET_TARGET_PROPERTIES(AlembicAbcCoreOgawa 
                        PROPERTIES DEFINE_SYMBOL
                        ALEMBIC_EXPORTS)
ENDIF()

INSTALL(FILES ${H_FILES}
        DESTINATION include/Alembic/AbcCoreOgawa)

IF (USE_TESTS)
	ADD_SUBDIRECTORY(Tests)
ENDIF()
