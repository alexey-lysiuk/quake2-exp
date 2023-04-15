cmake_minimum_required(VERSION 3.0)

project(Quake2 LANGUAGES C)

find_library(MATH_LIBRARY m)
find_package(CURL)
find_package(JPEG REQUIRED)
find_package(PNG REQUIRED)
find_package(SDL2 REQUIRED)
find_package(ZLIB REQUIRED)

if(NOT DCMAKE_BUILD_TYPE)
	set(DCMAKE_BUILD_TYPE Release)
endif()

add_library(game SHARED
	src/client/anorms.h
	src/game/game.h
	src/game/g_ai.c
	src/game/g_chase.c
	src/game/g_cmds.c
	src/game/g_combat.c
	src/game/g_func.c
	src/game/g_items.c
	src/game/g_local.h
	src/game/g_main.c
	src/game/g_misc.c
	src/game/g_monster.c
	src/game/g_phys.c
	src/game/g_save.c
	src/game/g_spawn.c
	src/game/g_svcmds.c
	src/game/g_target.c
	src/game/g_trigger.c
	src/game/g_turret.c
	src/game/g_utils.c
	src/game/g_weapon.c
	src/game/m_actor.c
	src/game/m_actor.h
	src/game/m_berserk.c
	src/game/m_berserk.h
	src/game/m_boss2.c
	src/game/m_boss2.h
	src/game/m_boss3.c
	src/game/m_boss31.c
	src/game/m_boss31.h
	src/game/m_boss32.c
	src/game/m_boss32.h
	src/game/m_brain.c
	src/game/m_brain.h
	src/game/m_chick.c
	src/game/m_chick.h
	src/game/m_flash.c
	src/game/m_flipper.c
	src/game/m_flipper.h
	src/game/m_float.c
	src/game/m_float.h
	src/game/m_flyer.c
	src/game/m_flyer.h
	src/game/m_gladiator.c
	src/game/m_gladiator.h
	src/game/m_gunner.c
	src/game/m_gunner.h
	src/game/m_hover.c
	src/game/m_hover.h
	src/game/m_infantry.c
	src/game/m_infantry.h
	src/game/m_insane.c
	src/game/m_insane.h
	src/game/m_medic.c
	src/game/m_medic.h
	src/game/m_move.c
	src/game/m_mutant.c
	src/game/m_mutant.h
	src/game/m_parasite.c
	src/game/m_parasite.h
	src/game/m_player.h
	src/game/m_soldier.c
	src/game/m_soldier.h
	src/game/m_supertank.c
	src/game/m_supertank.h
	src/game/m_tank.c
	src/game/m_tank.h
	src/game/p_client.c
	src/game/p_hud.c
	src/game/p_trail.c
	src/game/p_view.c
	src/game/p_weapon.c
	src/game/q_shared.c
	src/game/q_shared.h
)

add_executable(quake2
	src/client/anorms.h
	src/client/client.h
	src/client/cl_cin.c
	src/client/cl_demo.c
	src/client/cl_draw.c
	src/client/cl_ents.c
	src/client/cl_fx.c
	src/client/cl_http.c
	src/client/cl_input.c
	src/client/cl_inv.c
	src/client/cl_loc.c
	src/client/cl_main.c
	src/client/cl_newfx.c
	src/client/cl_parse.c
	src/client/cl_pred.c
	src/client/cl_scrn.c
	src/client/cl_tent.c
	src/client/cl_view.c
	src/client/console.c
	src/client/input.h
	src/client/keys.c
	src/client/keys.h
	src/client/mp3.h
	src/client/ref.h
	src/client/screen.h
	src/client/snd_dma.c
	src/client/snd_loc.h
	src/client/snd_mem.c
	src/client/snd_mix.c
	src/client/sound.h
	src/client/vid.h

	src/game/game.h
	src/game/m_flash.c
	src/game/q_shared.c
	src/game/q_shared.h

	src/include/minizip/ioapi.c
	src/include/minizip/ioapi.h
	src/include/minizip/unzip.c
	src/include/minizip/unzip.h

	src/linux/cd_linux.c
	src/linux/glob.c
	src/linux/glob.h
	src/linux/glw_linux.h
	src/linux/q2icon.xbm
	src/linux/qgl_linux.c
	src/linux/q_shlinux.c
	src/linux/rw_linux.c
	src/linux/rw_linux.h
	src/linux/rw_sdl.c
	src/linux/snd_sdl.c
	src/linux/sys_linux.c
	src/linux/vid_so.c

	src/qcommon/cmd.c
	src/qcommon/cmodel.c
	src/qcommon/common.c
	src/qcommon/crc.c
	src/qcommon/cvar.c
	src/qcommon/files.c
	src/qcommon/md4.c
	src/qcommon/net.c
	src/qcommon/net_chan.c
	src/qcommon/pmove.c
	src/qcommon/qcommon.h
	src/qcommon/qfiles.h
	src/qcommon/q_msg.c

	src/ref_gl/anormtab.h
	src/ref_gl/def_pal.h
	src/ref_gl/gl_decal.c
	src/ref_gl/gl_decal.h
	src/ref_gl/gl_draw.c
	src/ref_gl/gl_image.c
	src/ref_gl/gl_light.c
	src/ref_gl/gl_local.h
	src/ref_gl/gl_mesh.c
	src/ref_gl/gl_model.c
	src/ref_gl/gl_model.h
	src/ref_gl/gl_rmain.c
	src/ref_gl/gl_rmisc.c
	src/ref_gl/gl_rsurf.c
	src/ref_gl/gl_warp.c
	src/ref_gl/qgl.h
	src/ref_gl/warpsin.h

	src/server/server.h
	src/server/sv_ccmds.c
	src/server/sv_ents.c
	src/server/sv_game.c
	src/server/sv_init.c
	src/server/sv_main.c
	src/server/sv_send.c
	src/server/sv_user.c
	src/server/sv_world.c

	src/ui/qmenu.c
	src/ui/ui_addressbook.c
	src/ui/ui_atoms.c
	src/ui/ui_controls.c
	src/ui/ui_credits.c
	src/ui/ui_demos.c
	src/ui/ui_dmoptions.c
	src/ui/ui_download.c
	src/ui/ui_game.c
	src/ui/ui_joinserver.c
	src/ui/ui_keys.c
	src/ui/ui_loadsavegame.c
	src/ui/ui_local.h
	src/ui/ui_main.c
	src/ui/ui_multiplayer.c
	src/ui/ui_newoptions.c
	src/ui/ui_playerconfig.c
	src/ui/ui_quit.c
	src/ui/ui_startserver.c
	src/ui/ui_video.c
)

target_compile_definitions(quake2 PRIVATE
	GL_QUAKE
	USE_SDL
)
target_include_directories(quake2 PRIVATE
	${JPEG_INCLUDE_DIRS}
	${PNG_INCLUDE_DIRS}
	${SDL2_INCLUDE_DIRS}
	${ZLIB_INCLUDE_DIRS}
)
target_link_libraries(quake2 PRIVATE ${MATH_LIBRARY} JPEG::JPEG PNG::PNG SDL2::SDL2 ZLIB::ZLIB)

if(CURL_FOUND)
	target_compile_definitions(quake2 PRIVATE USE_CURL)
	target_include_directories(quake2 PRIVATE ${CURL_INCLUDE_DIRS})
	target_link_libraries(quake2 PRIVATE CURL::libcurl)
endif()

set_target_properties(game PROPERTIES
	LIBRARY_OUTPUT_DIRECTORY "$<TARGET_FILE_DIR:quake2>/baseq2"
	PREFIX ""
	SUFFIX .so
)
