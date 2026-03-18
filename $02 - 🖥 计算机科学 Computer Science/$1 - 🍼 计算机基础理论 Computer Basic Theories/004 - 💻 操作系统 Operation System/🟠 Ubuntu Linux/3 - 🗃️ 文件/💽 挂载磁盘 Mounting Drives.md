在Ubuntu系统内，所有存储器都需要预先挂载到一个目录才能被文件系统所访问。挂载磁盘可以使用`mount`命令手动挂载，也可以通过编辑`/etc/fstab`文件实现永久挂载

### 获取设备标识码

以超级用户权限运行时，`blkid`可以输出所有已链接的块设备（Block Device）的详细信息。这里的块设备指的是固态硬盘、磁盘、U盘、光盘映像等实体或虚拟的**储存设备**

```bash
sudo blkid
```

每一个储存设备显示的信息格式如下

```
/dev/nvme1n1p4: LABEL="Data" BLOCK_SIZE="512" UUID="D87213FE7213DFD4" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="c7526f66-5158-4c66-88ad-9fe2897ad09f"
```

+ **LABEL**：手动设置的名称
+ BLOCK_SIZE：空间大小
+ **UUID**：设备唯一标识码
+ **TYPE**：设备类型
+ PARTLABEL：分块名称
+ PARTUUID：分块ID

得到标识码，就可以编辑`/etc/fstab`文件了

### 编辑fstab文件

打开文件（`sudo nano /etc/fstab`），在里面增加一行，说明需要自动挂载的硬盘信息和挂载的选项，格式如下

```
<file system>          <mount point>   <type>  <options>       <dump>  <pass>
UUID=D87213FE7213DFD4  /media/Data     ntfs    default         0       1
```

+ **file system** - 设备标识码
+ **mount point** - 挂载目录，必须是空目录（一般放在`/media`内）
+ **type** - 设备类型
+ options - 读写限制
+ dump - 是否备份
+ pass - 启动检查的顺序

### 手动挂载

磁盘可以使用`mount`命令手动挂载，注意这个命令输入设备文件名而非UUID

```bash
sudo mount /dev/nvme1n1p4 /media/Data
```

取消挂载的命令是`umount`

```bash
sudo umount /dev/nvme1n1p4
```