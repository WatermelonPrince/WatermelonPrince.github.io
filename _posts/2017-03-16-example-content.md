---
layout: post
title: "Git的指令学习"
---


### 1.新建一个本地仓库

    $git init
    
### 2.配置仓库

* 告诉git你是谁

           git config user.name xxx
 
* 告诉git怎么联系你

            git config user.email xxxx

* 全局配置

          $ git config --global user.name xxx
          $ git config --global user.name xxx
          
* 如何学习git指令

  * 学习git 指令和svn指令是一样的，只不过展现的方式不一样，git 是通过使用指南的方式告诉我们如何使用。这个指南其实是一个不可编辑的vim。
  * git help + 指令
  * Q退出指南
  * 按空格下一页
  * control + b 上一页
  * / + 需要搜索的内容   可以进行搜索

* Git常规指令
    * 查看文件状态
    
            git status
            
    * 添加文件到暂存区
    
            git add xxx
            
       *  添加之前的颜色，红色代表工作区
       *  添加到暂存区之后的颜色，绿色代表暂存区
            
    * git commit 文件名称,如果么有在后面加上-m说明修改了什么，会自动进入vim界面。按i 进入编辑状态，输入完毕后，按esc,然后：wq保存退出。注意git中的add跟SVN中的add不一样，svn只需add一次，git每次修改之后都需要add。
      
    
            git commit xxx -m "修改日志"
            
    * git 中版本号是一个40位的哈希值，而svn中的版本号是一个递增的整数, git log  当前版本， git reflog  所有版本信息 ，
      * 已经提交,强制返回上一个版本

                git reset --hard HEAD^
                
                git reset --hard xxxxxx //前7位版本哈希值
                
      * 未提交，返回有以下两种方式：
      
                git checkout xxx //文件名
                git reset --hard HEAD //后面没有^本地回退
                
    * git diff + 文件名  查看指定文件的所有修改信息
               
             git diff xxx 
             
      * 如果显示绿色代表新增
      * 如果显示红色代表删除

### 3.远程仓库
#####svn需要一个单独服务器，git不需要，文件中，U盘中，云上，github,oschina

 * 新建git远程仓库，注意
  
        git init --bare  //注意这个仓库仅仅用于管理代码，不参与开发
 
 * 项目经理初始化项目,后面跟的是要克隆的远程仓库路径或者云上的仓库链接

 
        git clone xxxx 
        
 * 忽略不需要加入版本控制器的文件以及文件夹，.gitignore文件
   
   * 注意.gitignore文件需要与.git 文件夹在同一目录下
   
 * 新建项目，将代码提交到本地仓库
 
##### git中默认就会创建一个分支，这个分支叫做origin/master,相当于svn中的trunk
 
 * **注意** 和SVN一样，如果如果服务器仓库的代码被修改了，我们在提交代码也会报错。fetch first == out of data

##### 总结：git 和 SVN的最大区别
   1. **git每次修改新增都需要add**
   2. **git每台电脑都有一个仓库**        
   3. **git是先提交到本地仓库，再提交到远程仓库**

### 4.新人服务器的搭建
1. 新建一个新人服务器,初始化一个仓库。

        git  init --bare
        
2. 添加一个新的远程仓库 source control -> master -> config -> remotes -> add -> add remote。
3. 将最新的代码提交到新人服务器。
4. 分配新人服务器地址给新人。

### 5.git分支管理
1. 在本地代码库给项目打上一个标签
**（注意此时打上的这个标签仅仅是一个本地标签（和服务器没有关系）**

        git tag -a v1.0 - m "Version 1.0"
     
2. 将标签推送到远程服务器
   
        git push origin v1.0
     
3. 员工利用指令快速切换到1.0版本，开启一个新的分支，开始修复代码
   
        git checkout v1.0 //**根据提示：开启一个新的分支修复代码
        git checkout -b 1.0bug_fix
     
4. 修复完毕后,重复1，2步骤打新标签1.1的版本标签，将代码push到分支
5. 将代码merge到主分支后，然后commit到主分支，并push到服务器上 

**查看远程分支**

    git branch -r
 
**删除远程分支**：bug修改后此分支无用，可直接删除。

    
    git branch -r -d origin/bugfix1.0      
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     

    
            
      
            
            


