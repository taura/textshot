lib_LTLIBRARIES = libTraceInput.la
libTraceInput_la_SOURCES = sslog_trace_impl.c ../slog2sdk-1.2.6/src/logformat/trace/logformat_trace_InputLog.c
libTraceInput_la_CFLAGS = -I../slog2sdk-1.2.6/src/logformat/trace
# ACLOCAL_AMFLAGS = -I m4
dist_bin_SCRIPTS = sslog

sslog_trace_impl.c : untar
../slog2sdk-1.2.6/src/logformat/trace/logformat_trace_InputLog.c : untar
untar : ../slog2sdk.tar.gz
	cd .. ; tar xvf slog2sdk.tar.gz
	touch $@

sslog : sslog.in
	sed -e s%@bindir[@]%${bindir}%g $@.in > $@.tmp
	chmod +x $@.tmp
	mv $@.tmp $@
