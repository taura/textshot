slog2_dir=../slog2/slog2sdk-1.2.6
input_log_c=$(slog2_dir)/src/logformat/trace/logformat_trace_InputLog.c
lib_LTLIBRARIES = libTraceInput.la
libTraceInput_la_SOURCES = sslog_trace_impl.c $(input_log_c)
libTraceInput_la_CFLAGS = -I$(slog2_dir)/src/logformat/trace
ACLOCAL_AMFLAGS = -I m4
dist_bin_SCRIPTS = sslog

$(libTraceInput_la_SOURCES) : untar

sslog : sslog.in @compile_jumpshot_too@
	sed -e s%[@]libdir[@]%${libdir}%g \
		-e s%[@]jumpshot_dir[@]%${jumpshot_dir}%g \
		-e s%[@]default_jvm[@]%${default_jvm}%g \
		$@.in > $@.tmp
	chmod +x $@.tmp
	mv $@.tmp $@

compile_jumpshot_too : untar
	@echo '********** compiling and installing slog2 SDK **********'
	cd $(slog2_dir) && ./configure --prefix=$(jumpshot_dir)
	cd $(slog2_dir) && make
	cd $(slog2_dir) && make install PREFIX=$(jumpshot_dir)
	touch $@

untar : ../slog2/slog2sdk.tar.gz
	cd ../slog2 && tar xvf slog2sdk.tar.gz
	touch $@
