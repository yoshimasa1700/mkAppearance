# CMakeのバージョン
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

#SET(CMAKE_CXX_COMPILER "clang++")


# リリースビルド用オプション
SET(CMAKE_C_FLAGS_RELEASE "-Wall -O3")

# デバッグビルド用オプション
SET(CMAKE_C_FLAGS_DEBUG "-g")
set(CMAKE_CXX_FLAGS "")
set(CMAKE_CXX_FLAGS_DEBUG "-g -pg")
set(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-g -pg -O3")
set(CMAKE_CXX_FLAGS_RELEASE "-DNDEBUG -O3")
set(CMAKE_CXX_FLAGS_MINSIZEREL "")
SET (CMAKE_CXX_FLAGS "-pg")

# ビルドのタイプはリリース
SET(CMAKE_BUILD_TYPE Release)
#SET(CMAKE_BUILD_TYPE Debug)
# 環境変数の登録

# プロジェクト名
PROJECT(mkAppearance)

# 実行に必要なライブラリのパッケージを見つける
FIND_PACKAGE(OpenGL)
FIND_PACKAGE(GLUT)

# バージョン番号
# SET(serial "1.0.0")

# ビルドするためにインクルードするヘッダーファイルの場所
INCLUDE_DIRECTORIES("${PROJECT_SOURCE_DIR} /usr/local/include ${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS}")

# ライブラリの場所
LINK_DIRECTORIES("/usr/local/lib")

SET(SOURCE main.cpp)

# 実行ファイルを生成
ADD_EXECUTABLE(mkAppearance ${SOURCE})

# ライブラリとリンクする
TARGET_LINK_LIBRARIES(mkAppearance ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES} glm png jpeg)


# バージョン番号の適用
# SET_TARGET_PROPERTIES(objectPoseEstimation PROPERTIES VERSION ${serial})
# SET_TARGET_PROPERTIES(learning PROPERTIES VERSION ${serial})
