#  EC2_disk increasing

# First identify the disk type by df -Th command and check the disk size by comamnd lsblk

      root@btest:~# lsblk 
      NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
      loop0     7:0    0  55.7M  1 loop /snap/core18/2829
      loop1     7:1    0  55.4M  1 loop /snap/core18/2846
      loop2     7:2    0   104M  1 loop /snap/core/16928
      loop3     7:3    0  25.2M  1 loop /snap/amazon-ssm-agent/7993
      loop4     7:4    0  25.8M  1 loop /snap/amazon-ssm-agent/9565
      loop5     7:5    0 104.2M  1 loop /snap/core/17200
      loop6     7:6    0  74.3M  1 loop /snap/core22/1621
      loop7     7:7    0  73.9M  1 loop /snap/core22/1663
      xvda    202:0    0    25G  0 disk 
      └─xvda1 202:1    0    25G  0 part /
      xvdb    202:16   0    50G  0 disk /home
      root@test:~# df -Th
      Filesystem     Type      Size  Used Avail Use% Mounted on
      udev           devtmpfs  7.9G     0  7.9G   0% /dev
      tmpfs          tmpfs     1.6G  816K  1.6G   1% /run
      /dev/xvda1     ext4       25G   19G  5.4G  78% /
      tmpfs          tmpfs     7.9G     0  7.9G   0% /dev/shm
      tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
      tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
      /dev/loop0     squashfs   56M   56M     0 100% /snap/core18/2829
      /dev/loop2     squashfs  104M  104M     0 100% /snap/core/16928
      /dev/loop1     squashfs   56M   56M     0 100% /snap/core18/2846
      /dev/loop3     squashfs   26M   26M     0 100% /snap/amazon-ssm-agent/7993
      /dev/loop4     squashfs   26M   26M     0 100% /snap/amazon-ssm-agent/9565
      /dev/loop5     squashfs  105M  105M     0 100% /snap/core/17200
      /dev/loop6     squashfs   75M   75M     0 100% /snap/core22/1621
      /dev/xvdb      ext4       50G   27G   21G  57% /home
      tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/1066
      /dev/loop7     squashfs   74M   74M     0 100% /snap/core22/1663
      tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/1058
      root@test:~# date
      Tue Dec 31 02:14:27 UTC 2024
      root@test:~#


# in the above it is ext4 disk type

# Use the below command to resize the disk partitions 

            # Step 1: Resize the partition
            sudo growpart /dev/xvda 1
            
            # Step 2: Resize the filesystem
            sudo resize2fs /dev/xvda1  # For ext4
            # or
            sudo xfs_growfs /dev/xvda1  # For xfs
            
            # Step 3: Verify the size
            lsblk

# real change example 
            root@test:~# sudo growpart /dev/xvda 1
            CHANGED: partition=1 start=2048 old: size=52426719 end=52428767 new: size=104855519,end=104857567
            root@test:~# sudo resize2fs /dev/xvda1
            resize2fs 1.44.1 (24-Mar-2018)
            Filesystem at /dev/xvda1 is mounted on /; on-line resizing required
            old_desc_blocks = 2, new_desc_blocks = 4
            The filesystem on /dev/xvda1 is now 13106939 (4k) blocks long.
            
            root@test:~# date
            Tue Dec 31 02:19:24 UTC 2024
            root@test:~#

# after increased root partition disk

            root@test:~# lsblk
            NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
            loop0     7:0    0  55.7M  1 loop /snap/core18/2829
            loop1     7:1    0  55.4M  1 loop /snap/core18/2846
            loop2     7:2    0   104M  1 loop /snap/core/16928
            loop3     7:3    0  25.2M  1 loop /snap/amazon-ssm-agent/7993
            loop4     7:4    0  25.8M  1 loop /snap/amazon-ssm-agent/9565
            loop5     7:5    0 104.2M  1 loop /snap/core/17200
            loop6     7:6    0  74.3M  1 loop /snap/core22/1621
            loop7     7:7    0  73.9M  1 loop /snap/core22/1663
            xvda    202:0    0    50G  0 disk 
            └─xvda1 202:1    0    50G  0 part /
            xvdb    202:16   0    50G  0 disk /home
            root@test:~# df -Th
            Filesystem     Type      Size  Used Avail Use% Mounted on
            udev           devtmpfs  7.9G     0  7.9G   0% /dev
            tmpfs          tmpfs     1.6G  816K  1.6G   1% /run
            /dev/xvda1     ext4       49G   19G   30G  39% /
            tmpfs          tmpfs     7.9G     0  7.9G   0% /dev/shm
            tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
            tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
            /dev/loop0     squashfs   56M   56M     0 100% /snap/core18/2829
            /dev/loop2     squashfs  104M  104M     0 100% /snap/core/16928
            /dev/loop1     squashfs   56M   56M     0 100% /snap/core18/2846
            /dev/loop3     squashfs   26M   26M     0 100% /snap/amazon-ssm-agent/7993
            /dev/loop4     squashfs   26M   26M     0 100% /snap/amazon-ssm-agent/9565
            /dev/loop5     squashfs  105M  105M     0 100% /snap/core/17200
            /dev/loop6     squashfs   75M   75M     0 100% /snap/core22/1621
            /dev/xvdb      ext4       50G   27G   21G  57% /home
            tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/1066
            /dev/loop7     squashfs   74M   74M     0 100% /snap/core22/1663
            tmpfs          tmpfs     1.6G     0  1.6G   0% /run/user/1058
            root@bastion:~# date
            Tue Dec 31 02:19:54 UTC 2024
            root@test:~#
