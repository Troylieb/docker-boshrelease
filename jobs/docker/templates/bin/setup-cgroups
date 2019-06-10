for sys in $(awk '!/^#/ { if ($4 == 1) print $1 }' /proc/cgroups); do
	where=/sys/fs/cgroup/$sys
	mkdir -p $where
	if ! mountpoint -q $where; then
		if ! mount -n -t cgroup -o $sys cgroup $where; then
			rmdir $where || true
		fi
	fi
done
