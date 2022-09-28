BOOST_CXX = \
	-DBOOST_ERROR_CODE_HEADER_ONLY \
	-DBOOST_SYSTEM_NO_DEPRECATED \
	-DBOOST_COROUTINES_NO_DEPRECATION_WARNING \
	-DBOOST_ASIO_DISABLE_THREADS \
	-DBOOST_ALL_NO_LIB

bin_PROGRAMS = \
	netipmid

netipmid_SOURCES = \
	endian.hpp \
	socket_channel.hpp \
	message.hpp \
	session.hpp \
	sol/console_buffer.hpp

netipmid_CPPFLAGS = -DNET_IPMID_LIB_PATH=\"/usr/lib/net-ipmid/\"

netipmid_LDFLAGS = \
	$(SYSTEMD_LIBS) \
	$(CRYPTO_LIBS) \
	$(libmapper_LIBS) \
	$(PHOSPHOR_LOGGING_LIBS) \
	$(PHOSPHOR_DBUS_INTERFACES_LIBS) \
	$(LIBIPMID_LIBS) \
	-lboost_coroutine \
	-lchannellayer \
	-luserlayer \
	-lstdc++fs \
	-lstdc++

netipmid_LDFLAGS += ${srcdir}/netipmid-auth_algo.o
netipmid_LDFLAGS += ${srcdir}/netipmid-command_table.o
netipmid_LDFLAGS += ${srcdir}/netipmid-comm_module.o
netipmid_LDFLAGS += ${srcdir}/netipmid-crypt_algo.o
netipmid_LDFLAGS += ${srcdir}/netipmid-integrity_algo.o
netipmid_LDFLAGS += ${srcdir}/netipmid-main.o
netipmid_LDFLAGS += ${srcdir}/netipmid-message_handler.o
netipmid_LDFLAGS += ${srcdir}/netipmid-message_parsers.o
netipmid_LDFLAGS += ${srcdir}/netipmid-sd_event_loop.o
netipmid_LDFLAGS += ${srcdir}/netipmid-sessions_manager.o
netipmid_LDFLAGS += ${srcdir}/netipmid-sol_module.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-channel_auth.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-guid.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-IpmiLocked.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-open_session.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-payload_cmds.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-rakp12.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-rakp34.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-session_cmds.o
netipmid_LDFLAGS += ${srcdir}/command/netipmid-sol_cmds.o
netipmid_LDFLAGS += ${srcdir}/sol/netipmid-sol_context.o
netipmid_LDFLAGS += ${srcdir}/sol/netipmid-sol_manager.o


netipmid_CXXFLAGS = \
	-flto \
	$(SYSTEMD_CFLAGS) \
	$(BOOST_CXX) \
	$(libmapper_CFLAGS) \
	$(PHOSPHOR_LOGGING_CFLAGS) \
	$(PHOSPHOR_DBUS_INTERFACES_CFLAGS) \
	$(LIBIPMID_CFLAGS)

if HAVE_SYSTEMD
SYSTEMD_UNIT = phosphor-ipmi-net@.service
SYSTEMD_SOCKET = phosphor-ipmi-net@.socket
systemdsystemunit_DATA = $(SYSTEMD_UNIT) $(SYSTEMD_SOCKET)
endif  # HAVE_SYSTEMD

SUBDIRS = test

