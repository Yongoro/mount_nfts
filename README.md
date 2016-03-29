# Mount NTFS filesystem on centos 7

## Enable EPEL (Extra Packages for Enterprise Linux (Fedora Project)) repositories
### method 1
* using yum package manager

  as root, follow the commands
  ```
  yum -y install epel-release
  yum repolist
  ```
### method 2
* Install the extra EPEL repositories from dl.fedoraproject.org
  ```
  cd /tmp
  wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
  ls *.rpm
  sudo yum install epel-release-7.noarch.rpm
  sudo yum repolist
  ```
## Install package for ntfs

  ```
  yum install ntfs-3g ntfsprogs ntfsprogs-gnomevfs
  ```
## mount the NTFS filesystem
* creating the mounting point

  ```
  mkdir /mount/point/window
  ```
* editing /etc/fstab
    we suppose the filesystem to mount is /dev/sda1
    * read only
    
        ```
        /dev/sda1  /mount/point/window  ntfs-3g ro,umask=0222,defaults 0 0
        ```
    * read write
    
        ```
        /dev/sda1  /mount/point/window  ntfs-3g rw,umask=0000,defaults 0 0
        ```
    * mounting
    
      ```
      mount /mount/point/window
      ```
        
