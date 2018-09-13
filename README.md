# Laravel-Homestead-
Laravel Homestead notes

## vagrant操作命令
* 安装 Homestead Vagrant Box(国内只能呵呵，请使用离线安装)
> vagrant box add laravel/homestead

* 启动虚拟机
> vagrant up

* 删除虚拟机
> vagrant destroy --force

* 重新配置机器（在更新homestead.yaml后，务必通过运行）
> vagrant reload --provision

* 连接虚拟机
> vagrant ssh

* 更新Homestead（谨慎操作，国内网速～～）
> vagrant box update

## window下注意事项
* Laravel Homestead 离线安装
先下载好virtualbox.box，然后创建一个名为 metadata.json(这个文件放在你下载的virtualbox.box同一目录下) 文件，文件内容如下：

```
{
    "name": "laravel/homestead", // 名称尽量不要修改，如果修改了，vagrnat up 启动的时候会报错：box 'laravel/homestead' could not be found, 然后会自动下载0.4.0版本。
    "versions": [{
        "version": "0.5.0", // 你下载的 virtualbox.box 版本号
        "providers": [{
            "name": "virtualbox",
            "url": "file:///Users/zero/www/virtualbox.box"  // 这里是你下载的virtualbox.box 路径。
        }]
    }]
}
```

然后终端进入virtualbox.box所在目录：执行 `vagrant box add metadata.json`
vagrant box list, 可以看到： laravel/homestead (virtualbox, 0.5.0)， 如果出现laravel/homestead (virtualbox, 0)，请重装。
疑问： 如果 执行 vagrant box list 可以看到 laravel/homestead (virtualbox, 0.5.0) ，但在 vagrant up  阶段，出现  “box 'laravel/homestead' could not be found”  那么可以在Homestead目录下执行：vagrant init laravel/homestead，应该会解决问题。

<a href="https://www.cnblogs.com/zero-zf/p/6031965.html">参考</a>

* 共享文件夹必须使用window的目录格式,demo:
```
folders:
    - map: H:\phpStudy\PHPTutorial\WWW\test\laravel5.7 //必须使用window的目录格式
      to: /home/vagrant/code/laravel5.7
```

* 通过 BIOS 来启用硬件虚拟化 (VT-x)。如果您在 UEFI 系统上使用 Hyper-V，可能还需要禁用 Hyper-V 才能访问 VT-x

