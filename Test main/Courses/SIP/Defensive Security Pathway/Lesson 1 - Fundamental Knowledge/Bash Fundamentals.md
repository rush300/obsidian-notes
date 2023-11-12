# Introduction to Linux Shell

**What is Linux?**  

Linux is a completely free, open sourced operating system, created by a Finnish software engineer named Linus Torvalds in the early 1990s. An operating system is software that can directly manage your computer's hardware and resources, whether that is the CPU, graphics card, memory, etc. Since Linux is completely free and open sourced, anyone can install, modify, and change the source code. Even though Linux is completely free, it is licensed under a General Public License which means that you can freely change or even distribute code, but you must do so under the same license.

​

**How does Linux work?**

Even though Linux was developed and kind of designed to be similar to UNIX, Linux has evolved far from UNIX making it easily distinguishable between the two. Every Linux operating system works under something called the "Linux kernel" which is a main component of a Linux operating system and is the main interface between the computer's hardware and the processes. The kernel is made to communicate between the hardware and processes to make managing resources efficient as possible.

The Linux operating system comes with core components amongst the installation that give the user a way to manage resources from the kernel, installing new software, configure settings, etc. Everything downloaded from the installation of Linux bundled together makes the system a functional operating system.

​

**How is Linux Different from Other Operating Systems?**

Like we covered before, Linux is completely free and open-source. Other operating systems like Mac and Windows aren't open-source so this makes Linux more appealing just from that.

Linux fundamentally uses a lot less resources just to run the operating system compared to Windows and Mac.

Linux is used widely by multiple big name companies whether its NASA, web servers, google, or even ATM machines.

​

**Linux VS Windows**

The main difference between Linux and Windows is that it has a faster development. Since Linux is open-source, contributors from all over the world are able to speed up its development process. Windows releases a new kernel about every 3 years and Linux releases a new kernel about every 3 months or less.

​

Linux is way more secure than Windows because of how Linux manages account privileges within the system.

Linux is way more customizable than Windows. For one, it has so many different distributions that offer different customization capabilties.

​

**Linux VS Mac**

Linux and Mac are similar in one specific way. They both have operating systems that are based off of UNIX, only difference is Mac uses a version of UNIX called the Berkeley System Distribution (also known as BSD).

​

Linux is also more secure than Mac, and is free to use unlike Mac. This is very similar to the comparison with Windows.

​

**What is a Linux Distribution?**

A Linux distribution is a version of the open source Linux operating system that is based off of the Linux kernel that is packaged with other components, which is usually a package management system.

​

This can leave you with the question of, "what Linux distro is good for me?" It all comes down to what your skill level is and you goal with Linux. If you are new to Linux a good starting distro would be Ubuntu. Ubuntu is one of the best distributions and is popular because it provides a very stable experience.

​

There are many distributions out there, there are over 500+ published distributions under the General Public License.

# Linux Terminal Productivity

In this section of the course we will be talking about Linux Terminal Productivity. I will give you some tips and tricks on what you can do to make your life just a little bit easier when navigating the Linux Terminal.  

​

**Productivity Tools**

1. Terminator / tmux

- Terminator and tmux is an application which allows multitasking in the terminal window. When you install Linux, you are left with a terminal that uses tabs instead of multi-purpose boxes like Terminator and tmux does. I recommend strongly downloading both of these and picking between the two which one you like better.
- For Terminator you can split your terminal with either right clicking your terminal and selecting the splitted options, or use the keybinds like Ctrl+Shift+O and Ctrl+Shift+E . To close a tab, use Ctrl+Shift+W

1. Git Branch

- You can start a Z shell and will see the name of your current branch and if you have any changes in your code that aren't saved. It's a lot more useful if you deal with Git Branches in Z shell.

https://ohmyz.sh/

1. KDE - Desktop Customizer

- Simply just a desktop customizer, it's my favorite and helps when I have multiple things open. It's kind of close to PowerToys on Windows if you've ever used it.

https://kde.org/

1. xclip / outputing a command into a file

- This helps you send output of a command directly to a clipboard, download it with sudo apt install xclip . After you type a command out, use | xclip and it will output your command results to your clipboard ready to be pasted.
- I only use xclip whenever I can't output a command's results into a file with either tee -aor >> filename.txt

1. Nerd Font

- Nerd Font is exactly what the name is, a font for nerds! But on a serious note, it basically just adds different fonts/colors to anywhere of your choice on your system. It's very aesthetically pleasing.

(These are just a few tools but in my opinion the most useful for high-demand overall usage. If you need to go more in depth for what tools can help you be productive, google something like "linux video editing productivity")

​

**Repeating Past Commands**

- Don't feel like typing up that big command you just did again? Simply click the UP arrow on the keyboard.

  

**Fast Command Usage**

- When typing a command, simply hit tab to auto-finish what you were typing. With the new version of 2021 Kali Linux, it even shows you in a light font what it will auto-complete with using Tab.
- When you want to change something in your command, click Alt+Backspace to delete 1 word at a time. You can also use Ctrl+ArrowKey to move to the beginning or end of a word in your terminal.
- Do cd - to quickly go back to your past directory.
- Do cd to quickly get to your home directory

  

**Using Aliases**

- Aliases allow you create quite literally an alias for a command in your terminal. For example if I wanted to make an alias to make the command ls do ls -la , I would simply run alias ls="ls -la"

  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.filestackcontent.com/Lm1s3dsSQtKVNjfX3coY)

# Package Managers & File Archiving

**What is a Package Manager?**  

A package manager in Linux is basically just a tool that allows you to install, remove, configure, and control software packages on the operating system.

​

**How does a package manager work?**

Most package managers are used in the command-line interface.

If you didn't know, apt-get is a package manager. Whenever you install something on Linux with that command, it's searching all of the packages included with the install portion of the command to install what you need.

​

**What is a package?**

A package in Linux is is anything that is an application that can be ran in a GUI, a software, or a CLI tool. These applications consist of a collection of files that work together to perform a task.

​

**Why do packages exist?**

Every Linux operating system uses a different software that uses a different kernel. (we covered this in a past section) Packages include a distinct usage of dependencies that have to fit the packaged software to be able to run a program correctly on that given operating system.

​

**What is archiving?**

Archiving is when you combine multiple files and even directories into one file. It's mainly used to backup your information or when you want to move data from one destination, to another. A lot of people get archiving confused with compressing, compressing is when you reduce the size of a file or directory.

​

**How do I archive?**

The most common/popular programs used to archive files and directories are

- tar
- zip

Between the two programs, I find tar to be easier to use compared to zip. It's just conveniently better in my opinion.

tar comes preinstalled on almost every Linux distribution, and to learn how to use it you can easily do tar --helpin your console.

​

**tar VS zip**

The main difference between tar and zip is zip's compression is built-in and happens for every single file that you archive. tar on the other hand, compression is an extra step that you need to take to compress the entire archive.

​

The main takeaway is to just understand that:

**tar =** uncompressed archived file

**zip =** compressed archived file

# Command Line Chaining

**What is Command Line Chaining in Linux?**  

Chaining in Linux is when you combine multiple commands and make them perform based on the order you execute them in. Imagine writing a short shell script in your terminal but you're actually executing it directly from the terminal.

For example, our Bug Bounty tool uses a bash script to execute multiple different commands in the same manor. It uses different tools that each has their own command chaining to perform different tasks at the same time.

​

**What are the Command Line Chaining Commands?**

- PIPE: |

The PIPE operator in my opinion is the easiest and most useful command chain because it takes the output of the first command and works as an input for the second command.

example: cat text.txt | wc -l

- Ampersand: &

The Ampersand operator is used to either run one command in the background or make two or more commands run in the background at the same time.

example 1: nmap 192.168.0.1 &

example 2: apt-get update & apt-get upgrade &

- AND: &&

The AND operator is used to execute only the second command if the first command works.

example: apt-get update && apt-get upgrade

- Semi-Colon: ;

The Semi-Colon operator allows you to run several commands in a single execution, consecutively.

example: apt-get update ; apt-get upgrade ; cd tools

- OR: ||

The OR operator is used very similarly to an else statement in programming. It's used to execute the second command only if the first command fails.

​

For example, imagine trying to execute the command passwd user without having root permissions. The first command will fail and the second one will execute.

​

example: passwd user || nmap 192.168.0.1

​

These are in my opinion the most popular command line chaining commands. There are a few more for example, !, {}, \\, etc.

# System Hardware & Time Examination

In a past section, we learned about what the operating system is, the general public license, and the kernel. We didn't yet discuss the boot loader.  

​

The bootloader, installs the operating system into the computer's memory. When you first power on the system, there's a basic input/output system that runs some basic tests to test your computers infrastructure to boot the operating system.

​

Unlike Mac and Windows, Linux requires you to install a separate bootloader to run any distribution. Most distributions have you select either GRUB or LOAD when you are installing the distribution.

​

**Recommended Minimum System Requirements**

- 4 GB RAM
- 25+ GB of disk space
- 2 GHz dual core processor

  

**Time Examination - Problem-Solving Mindset**

- Realize your problems
- Focus on a solution
- Come up with many different solutions
- Implement these solutions and see if they work

  

# Disks & File System Permissions

**Disks in Linux**  

Disk layout is very important in Linux and a lot of people don't realize it. Every hard drive partition, floppy disk, or compact disc all have a file system on them. What happens is you create a single "tree" of the filesystem by mounting the filesystem on your device which is called the mount point.

​

Your operating system mounts your filesystem when you first install Linux as /. But, at the same time you can mount your partitions as other things like /home,/tmp, etc. You can also mount files from other devices using something called a networked filesystem (NFS).

​

**CD-ROM**

CD-ROM stands for a compact disc used as a read-only optical memory device for a computer system. Whenever you mount the root file system and want to use CD-ROM, the mount point must exist before you mount the CD-ROM over the mount point. When the CD-ROM is mounted, the files and directories become the files and directories under the /cdrom subdirectory.

​

Any files that were already in your /cdrom subdirectory won't be there anymore, but they still exist on the mount point that you have. To visit these files, you would have to unmount the CD-ROM.

​

**Creating and Partitioning a Disk**

There is a lot of ways you can partition a disk in Linux, a lot of the popular tools are GNU Parted, Fdisk, Gparted, etc.

Usually a lot of people use Oracle VM Virtual Box for their host to their Linux system and sadly, it's not as easy as you'd think to add space to your system. You can go to the settings and allocate more space but it doesn't link with your iso file after your first time installation. This is a step of the process but you actually need to go into the terminal and use a tool like Fdisk or Gparted to allocate the unallocated space.

​

- First, run Fdisk or Gparted and resize/move your /dev/sda .
- If you're using Gparted, all you have to do is drag the arrow key to the end or up the New Size field.
- Hit apply and there should be a new partition for more space

  

**Linux File System Permissions**

Linux has three user types on the Linux system. It uses something called a "multi-user system" that uses specific permissions for security. These three user types are the user, group, and other. These three user types are divided into permissions that are read, written, and executed under the r w and x letter.

​

Have you ever done ls -la and saw those random r w and x permissions on the left side? That's how Linux reads how to execute the files or subdirectories.

- r = read (open)
- w = write (save)
- x = execute

  

**chown**

The chown command can change the owner and/or group of each FILE to OWNER and/or group.

This basically allows you to change the ownership of a file or directory.

​

**chmod**

The chmod command is used to change the access permissions of files and directories.

​

**chown VS chmod?**

To keep it short and sweet, use chown whenever you need to change one of the 3 user types (user, group, and other) to one or another.

​

Use chmod whenever you need to change the file permissions to read, write, or execute.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.filestackcontent.com/QkL2ehdjSgKLouAzVuee)

# Processes, Services & Performance

**What is a process?**  

A process is an instance of a running program. Every single time you run a command in your terminal, a particular program is ran and a process is created for it.

​

This is called a PID. Each process in Linux has a PID and it is created to associate itself with a particular user and group account.

​

Linux can run multiple programs at the same time, which makes these processes categorized as 'tasks'.

​

A good skill to know in Linux is how to manage the processes running currently on your system. To do so, ps aux takes a quick screenshot of your processes and spits it out in your terminal.

​

ps aux will tell you what user is being used to run a certain program, the PID, the % of CPU usage, the % of memory usage, your VSZ (virtual set size), your RSS (resident set size), TTY (TeleTYpewriter), the STAT, when the process started, how long it's been running, and what command was used to execute the command.

​

**What is a Linux service?**

A Linux service is a program that can run in the background of your system. Linux automatically launches a select amount of programs on startup of your system to ensure security for crucial operations of your system.

​

One main service in Linux that we will cover are daemons. Daemons are usually instanced as a process which we already covered, but the main difference is they run quietly in the background rather than under the direct control of a specific user group.

​

**Listing Services in Linux**

If you do a command like sudo systemctl --type service -all you will be able to see all the services that are on your system.

​

If you try it, you will be able to see a bunch of enabled/disabled markers statusing whether these services are currently active or not.

​

Then you have static and generated status codes. Static means they will only be used if another service needs it. Generated is for services that need a systemd generator.

​

Now for example lets say we wanted to see only services on your system that are currently active, we would need to run a command involving the pipe chain command (which we learned in a past lesson)

​

sudo systemctl | grep running

​

**Managing Services in Linux**

It's very important to understand how to manage what is running on your system especially if you are interested in becoming a Linux Administrator.

​

The most important commands to understand for starting and stopping services in linux are

​

sudo systemctl start <service name>

sudo systemctl stop <service name>

​

Keep in mind, if you don't know how to name a service, run the command we learned from Listing Services in Linux, and then just copy paste the services names.

​

You can also enable/disable a service with

​

sudo systemctl enable <service name>

sudo systemctl disable <service name>

  

This may leave you wondering, what's the difference between start/stop, and enable/disable?

  

It's easy, enable/disable is telling your system whether or not you want a service to run when your system starts up.

​

You can also check statuses of services by running:

​

sudo systemctl status <service name>

​

**Linux Performance**

Just like I mentioned with services in Linux, it's important to understand the performance in Linux if you want to become an Administrator.

​

In my opinion, there is one command that is the best over the rest for Linux performance. That is the top command. It shows you your memory usage, CPU usage, buffer sizes, PID, cache sizes, commands used to execute, etc.

​

The top command is very useful for Linux Sys Administrators because it allows you to monitor the system in live time.

​

(An alternative that some people like is Htop , it's very similar to top but it is an advanced version.)

​

**Netstat**

Netstat is kind of related to top but it lets you monitor incoming and outcoming network packets. It's also another really good tool for a Linux Sys Admin.

# Managing Users & Groups

**Managing Users & Groups**  

Just like managing Linux processes, services and performance, users & groups are just as important. When you are a Linux Administrator, you might have to administer a Linux system that has multiple users.

​

Lets say you are at a work laptop with Linux as the main OS and your boss wants you to add your new co-workers Bob and Jim to the computer.

First you're going to have to create the users with their usernames of Bob and Jim, then create their groups relating to their role in the company.

​

**Creating/Managing The Users**

Since you would be adding these two users to a work computer as a Linux Administrator, it would probably be in your best interest to add their own home directories as well.

- Bob: sudo useradd -m Bob
- Jim: sudo useradd -m Jim

  

Now, both users would be created and if you look in the home directory you will see both Bob and Jim having their own directories because of the -m command.

But, what about a password for each user? There needs to be some security.

- Bob: sudo passwd Bob
- Jim: sudo passwd Jim

  

After typing each command you will have to enter their new password in the field for each user.

  

**Adding Groups**

Let's say for example Bob is going to be managing the Services on that Linux computer. Simply add a new group like this:

- Bob: addgroup BobServices

For another example, lets say Jim will be managing the Processes.

- Jim: addgroup JimProcesses

With these two new groups created, lets say you wanted to assign each user to each group.

- Bob: sudo usermod -a -G BobServices Bob
- Jim: sudo usermod -a -G JimProcesses Jim

  

**Adding The Permissions For Each Person**

Now that each user has its own username, password and group, it would be a good time to assign permissions for each users directory.

​

Like we went over earlier, when you added each user to your Linux system, it created a directory in the home directory for each user.

​

You can assign each user to a directory for specific permissions with:

- Bob: sudo chown -R :BobServices /Bob

  

This basically just allows all members (Bob) of the /Bob directory to actually access that directory.

​

Now, let's say you want to add read and write permissions to the directory. Do so with:

sudo chmod -R g+w /Bob

Now, you can prevent any user not in the /Bob directory from accessing any file in the directory with:

sudo chmod -R o-x /Bob

  

This is a very broad explanation to managing users & groups with Linux, you can add and remove many different roles/permissions for each user in its own special way.

​

To learn more about the commands we covered (useradd, passwd, addgroup, usermod, chown and chmod) you can easily run man <command> to learn more about each command.

# Networking

**What is Networking?**  

Networking relates to when a computer is connected to devices and IoT devices that are able to communicate with one another.

​

You may ask, how is this related to Linux?

Since Linux was released, it has helped provide a strong set of networking related tools that provide the ability to manage DNS, routing, bridging, DHCP, managing packets, monitoring your network, etc.

We will mainly be covering DNS, routing and iproute2 in this section, but there will be other important topics brought up.

  

Networking has so many aspects to it and it's a very broad subject but I will be explaining what I think is most important.  

Networking Basics in Linux

- Square one to networking on Linux is the command ifconfig

  

ifconfig stands for interface configuration and it's supposed to be used to actually assign IP addresses to interfaces and enable/disable interfaces.

​

Mainly it's used to view the IP addresses or MAC addresses of your system.

Enable/disable interfaces with ifup eth0 and ifdown eth0 (eth0 is just an example, it shows you what kind of connection you're working with on the left hand side of the command's output.)

​

Assign IP addresses with ifconfig eth0 <example ip> netmask <example netmask> keep in mind though that the setting gets removed when your system restarts.

- iproute2

  

Unlike ifconfig and other basic tools, iproute2 combines the main tools you would use to control traffic in Linux.

Even though we just went over ifconfig , it is very incompetent to the abiltiies of iproute2 . iproute2 can basically do what any other tool does, but better and easier.

  

A few examples are:

ifonfig to ip addr or ip link

route to ip route

netstat to ip -s or ss or ip route

  

**DNS**

DNS stands for Domain Name System and it is a naming system for almost anything on the internet, it provides your browser a connection to the domain names on the servers.

​

On each Linux operating system, there is a specific file located in the /etc directory that shows you your DNS server IP address.

​

Use the command cat /etc/resolv.conf to show what your system uses for its name server.

​

If you own a website or are curious what their name server is, you can use tools like dig ,traceroute and nslookup to find out more information about their name server.

​

_examples:_

dig site.com

traceroute site.com

nslookup site.com

​

Also, if you really want to, you can change locations of your name servers in your /etc/resolv.conf file.

​

If you nano into it and change your server address to a data center in a different area, this can provide you some anonymity.

​

**For you Bug Bounty Hunters**

Does the knowledge of networking help in bug bounties?

​

When you are searching for vulnerabilities within a program, system or application, the knowledge of networking can actually be very useful. Whether it's subnetting, supernetting, communication protocols, status codes, http methods, etc.

# IPTables Firewall

**What is IPTables Firewall?**  

IPTables is a firewall program made specifically for Linux. It monitors traffic like any other firewall but it uses tables. The tables consist of rules called chains that will filter incoming/outgoing data packets.

​

**How does it work?**

Internet traffic is made up of packets that is sent over a network. These packets get broken up and put back together for IPTables to identify what to do with it.  

IPTables filters their packets with these set of rules:

- Chains: Chains are a string of rules, these string of rules control the aspect of when a packet is received IPTables finds the appropriate table and runs it through the chain of rules to see if it can find a match.
- Tables: Tables are files that hold information of several Chains.
- Targets: Targets are whether IPTables is going to deal with the packet or not. Meaning if they want to deal with the packet and put it through the chains or drop/reject it.
- Rules: Rules is the statement that tells your system what it needs to do with a packet. Rules are able to block or forward certain kinds of packets, the outcome of this rule set is called a Target.

  

**In-depth about Tables and Chains**

- Filters: Filters are the most frequently used within the default tables. It allows traffic in and out of your network.
- Input: This is where the chain controls the packets receieved by the server.
- Output: This is where the chain controls outbound traffic.
- Forwarding: This is where rules can control how the packages get routed through the server.
- Network Address Translation: Network Address Translation allows routing packets to networks that actually can't be accessed directly.
- Prerouting: This is where the chain assigns packets right when the server gets them.
- Postrouting: This is where the chain allows making changes to packets once they leave the output chain.

  

**How to install IPTables for Linux**

- update real quick with sudo apt-get update
- sudo apt-get install iptables
- If you want to keep the default firewall rules online when you reboot your system, do this command: sudo apt-get install iptables-persistent
- If you want common ports like 80 (http), 443 (https), and 22 (ssh) to continue working you have to allow IPTables to open these ports. (if you haven't realized by now, IPTables takes a lot of precautions for security) sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT Obviously for each other port number you change the 22 to whatever port number you need specifically.
- Allow traffic to your LOCALHOST sudo iptables -A INPUT -i lo -j ACCEPT
- Flush all rules for a clean slate with sudo iptables -F

  

**IPTables Essentials (in depth to commands)**

https://github.com/trimstray/iptables-essentials

On this github page this user provides many useful commands/tools (technically essentials) to configure your IPTables.

# Shell Scripting & Task Automation

**Shell Scripting**  

The shell that we use day to day is a real programming language. When you make scripts for shell, it is just a list of commands that are being executed in sequence.

​

A shell is basically just an interface in the Linux system because it gathers input from the user and executes that code based on your input. When the user's code finishes executing, it will display the output.

​

Shell's are great because it's an environment where us users can run our programs, commands, or scripts.

​

**Types of Shells**

The types of shells are pretty narrowed down to the two major forms of shell instances.

1. The Bourne Shell - $ character is the prompt symbol in the terminal
2. The C Shell - % character is the prompt symbol in the terminal

  

The Bourne Shell actually was the first shell that came with Unix.

​

Also, The Bourne Shell is by default installed at /bin/sh which makes it easy to call that location for writing bash scripts.

  

**Scripting in Bash**

Like we discussed earlier, bash is used in the normal shell whenever we are navigating it. To put this code into a script, it's very similar to just executing commands in your shell but they're sequenced.

​

In bash, loops allow us to go through our files to read and store data, go through variables, and even functions.

Right here I have a simple bash script that will echo a line of text, for example, let's name this file text.sh

​

**Bash Script Example:**

_nano text.sh_

_#!/bin/sh_

_echo "I love DC CyberSec Courses!"_

_Ctrl+X_

_Y_

_Enter_

_chmod +x text.sh_

_./text.sh_

​

This example takes you through exactly what you would need to do to make a very simple bash script.

​

Notice how you could literally just type echo "I love DC CyberSec Courses!" in your terminal and get the same output as the script.

​

To put a script to more use, add more lines of code, create functions, loops, variables, etc.

​

**Basic Operators (math) in shell**

Bash Script Example: (without nano/chmod instructions)

_#!/bin/sh_

_val=expr 50 - 25_

_echo "Answer : $val"_

  

Having val being our value, we set the command to execute with , and then executed our value with echo.

​

You can only access a value that is stored in a string with its name and prefix ($)

  

**Relational Operators**

The Bourne Shell can execute relational operators that are sepecifc to number values. These operators don't work for string values unless that value is a number.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.filestackcontent.com/BbVV1W2sRWGKhvP8F9yV)

**Basic Variables in shell**  

A variable in bash is nothing more nothing less than a piece of data that points to the actual information.

​

A variable can contain only letters, numbers, and an underscore.

​

Example of variables:

_VARIABLE__

_VARIABLE_1_

_Variable_4_B_

  

There are a lot of things you can do with variables, something that I find very useful alongside of accessing your values with variables (covered in basic operators) is read-only variables.

​

Example of read-only variable:

_#!/bin/sh_

_FOOD="Apples"_

_readonly FOOD_

_FOOD="Oranges"_

  

When you run this you will get an error saying "FOOD: is read only" and this might trick someone into thinking they don't have permissions to execute a file; but the code is what isn't executing!

Using Shell Arrays

​

A shell array is able to hold multiple values at the same time. Shell arrays provide a method of grouping a set of variables instead of creating a new name for each variable that you have to require, you're able to use a single array that stores all of your other variables.

​

Let's assume you are trying to set a various number of foods as a set of variables. Each variable is a scalar variable.

​

Example of defining array values:

_NAME01="Apples"_

_NAME02="Oranges"_

_NAME03="Bananas"_

​

Each single array stores the mentioned foods above, and it is able to follow a simple method to create something called an array variable.

​

array_name[index]=value

​

It's as simple as setting the name of your array, index is what the shell indexes the item in the array that is set, and value is the value you want them to be set at.

How does shell make decisions?

​

When you are making a script in bash, there might be situations where you need something to adapt one path out of the two given paths. To do so, you make use of something called conditional statements and these statements allow your program to make correct decisions and perform the correct procedures.

​

The Unix shell uses these two main statements:

The else/if statements

The case/esac statements

  

**Else/if Statements**

Else/if statements is useful decision making statement that is used to select an option from another set of options.

​

Example of else/if

_if echo "hello"_

_then_

_else echo "bye"_

_fi_

​

This is how bash reads an else/if statement.

​

The if statement is a keyword followed by a conditional expression and then the then keyword. The statement executes with the fi keyword.

​

**Bash Scripting Cheatsheet (best one)**

https://devhints.io/bash

​

Bash Script Examples (easier to read compared to the samples I made)

https://linuxhint.com/30_bash_script_examples/

​

**_Takeaway notes~_**

With everything we learned here about bash scripting, it goes to show how you can tie together normal command line inputs to chain with each other and execute together. It can save a lot of time with daily tasks especially if you are a System Administrator and need to run a daily routine of tasks.

  

# Practice Time! Over The Wire

Now it's your time to practice your skills learnt in this course by following along the "Over The Wire - Bandit" guide. Get started by downloading the guide below.

Download

[Over_The_Wire_-_Bandit.pdf](https://cdn.fs.teachablecdn.com/p6Ki6hhtS2KlzktypExp)

## Lesson Summary

The text provides an overview of several topics related to Linux:

- Linux is an open-source operating system that is free to use and can be customized by anyone
- Linux Terminal Productivity can be enhanced through tools like Terminator, tmux, KDE Desktop Customizer, xclip, and Nerd Font
- Command Line Chaining allows for the combination of multiple commands
- Package managers like apt-get are used to install and manage software packages
- Disk layout and file system permissions are important aspects of Linux
- Linux uses user, group, and other permissions to control access to files and directories
- Processes are instances of running programs in Linux and can be managed using the "ps aux" command
- Services are programs that run in the background, and daemons are a type of service that run quietly in the background
- Monitoring system performance is important for Linux administrators, and the "top" command provides information about memory and CPU usage
- Networking in Linux involves managing IP addresses and DNS
- The IPTables firewall is a firewall program used in Linux to filter network traffic
- Shell scripting allows users to create scripts in the shell, which are lists of commands that are executed in sequence
- Bash is a type of shell commonly used in Linux
- The text also provides an overview of the challenges and techniques used in the Over The Wire - Bandit challenge

Overall, the text provides a comprehensive introduction to various aspects of Linux and its management, including processes, services, performance, networking, firewall, and shell scripting.