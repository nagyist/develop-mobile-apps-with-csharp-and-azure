# Introduction

Welcome to my first book.  It's free, it's open source, and it's comprehensive.
Those attributes also describe two of my favorite technologies, and I'm basing
my first book on them.  The first is [Xamarin Forms][1] , a technology that
allows you to develop cross-platform mobile applications using C# and the .NET
framework.  The second is [Azure Mobile Apps][2], a technology that allows
you to connect your mobile app to  resources that are important in cloud
connected mobile applications such as table data, authentication, and push
notifications.

This book does not tell you everything there is to know about either topic.  It
focuses on the topics necessary to get your mobile apps connected to the cloud.

## Who is This Book For?

This book is for intermediate to experienced C# developers who have already
built a mobile app with Xamarin and want to take their mobile apps to the next
level by utilizing cloud services.

This book is not for the beginner.  Explicitly, I already expect you to know how
to develop C# and ASP.NET.  If you are unfamiliar with the C# language, you can
get started with a free course on the Internet.  The basics of the language can
be learned at [www.learncs.org][3].  Once you have the
language basics under your belt, you can move on to ASP.NET. There are some good
tutorials at the [asp.net][4] website.  Finally, you will want
to develop a mobile app without the cloud before moving on to the cloud
connection.  You can learn more about developing cross-platform mobile
development with Xamarin at the [Xamarin][5] website.


## What are Cloud Connected Mobile Apps?

I guess I should define some of the terminology that I am going to use.  When I
refer to a **mobile application** or **mobile app**, I mean every piece of
software that is related to the application you want to use.  This includes, for
example, the **mobile client**. This is the piece of code you run on your iPhone
or Android phone.  It also includes the **mobile backend** which is the service
that you run in the cloud to provide important services to your mobile client.

A **cloud connected mobile application** is a mobile client that connects to a
mobile backend for shared services.  Quite a few of the apps on your phone are
cloud connected already.  For example, Instagram uses the cloud for photo
storage, and Facebook uses the cloud to store the news feeds of you and your
friends.

## Features of Cloud Connected Mobile Apps

A cloud connected mobile application will use one or more services in the
following areas:

* Authentication
* Storage of structured data (like a task list)
* Storage of unstructured data (like photographs)
* Push notifications
* Invocation of Custom Code

I am going to cover each of these in great detail.  In addition, I will also
cover some common issues and solutions that developers run into while developing
cloud connected mobile applications such as testing and going to production.  

Aside from the actual features of mobile apps, there are other things to
consider while developing your mobile application.  Here is my list, in no
particular order:

1. Continuous Deployment
2. Slots or Staging Sites
3. Automatic Scalability
4. Database Backups
5. Combined Web

The point here is that my intent is to write a production quality application.
I need to be able to deploy my site with confidence without resorting to jumping
through hoops.  I want to run multiple versions of the backend so that I can run
a staging site for testing purposes.  I want to be able to roll back my
production site to a previous version at a moments notice.  I want to be able to
handle the load when my app is successful, and I want things to be backed up
(since bad things inevitably happen when I am least prepared).

All of these features are available in Azure App Service, and the Mobile Apps
SDK that I will use throughout the book is supported only on Azure App Service.

## What You Will Need

All the software you need to develop compelling mobile applications is available
for free on the Internet.  The hardware needs is pretty basic. You will need a
PC or a Mac.  If you intend to build and distribute iOS applications, you will
need a Mac.  Similarly, if you intend to build and distribution Universal
Windows applications, you will need a Windows 10 PC.  I do all my development
using a combination of both.  I have a [Mac Mini][6] to build my iOS applications,
and a beefy [Windows 10 PC][7] to build my Universal Windows and Android
applications.  I do all of my development using my Windows 10 PC.

In terms of software, you should have the following:

#### On your Mac

Your Mac should be running the latest version of Mac OSX and you should have
installed [XCode][8] from the Mac App Store.  You can't just install it though.
You need to run it at least once so you can agree to the license.

You should also download and install [Xamarin Studio][9] even if you intend to
develop all your code using the Windows 10 PC.  Xamarin Studio provides the
tools for compiling iOS and Android apps on a Mac.  If you wish to develop
mobile apps on your Mac, it also includes an Integrated Development Environment
(IDE) specifically for this.

If you intend to build Android applications on your Mac, you will also need to
download and install [Android Studio and Tools][21].  This is not required if
you intend to build your Android applications on your Windows 10 PC with Visual
Studio.

#### On your Windows 10 PC

Your Windows 10 PC should also be running the latest version of Windows 10. Make
sure you have automatic updates turned on.  In addition to Windows 10, you will
want to turn on Hyper-V. The installer for Visual Studio will do this for you if
necessary.  If you do not turn on Hyper-V, you will not be able to use the
Visual Studio Emulator for Android.  This emulator is superior to the emulator
that is supplied with the Android Toolkit.

Aside from Windows 10 and Hyper-V, you will need to download and install
[Visual Studio Community][10] and the [Azure SDK][11].  If you have access to
a higher edition of Visual Studio, that will work as well.  If you have already
installed Visual Studio, you may want to re-run the installer to add the Mobile
development components.  You want to request the installs for Web applications
and cross-platform mobile development.

> Development Tools are big, multi-gigabyte installers.  If you are on a slow or
restricted link, you may want to download the installers onto a thumb drive for
local installation.

Once you have downloaded and installed everything (Xcode, Xamarin Studio and
Visual Studio), go to the updates section for each tool and ensure they are
updated to the latest editions.  Small bugs tend to be fixed and never noted in
the description of the updates.  Nothing is more infuriating than bumping into a
bug without realizing that it has already been fixed and the problem is not
really your fault.

#### Other Learning

Before you get started with development, spend some time learning the tools of
the trade.  The command prompt on the Mac is [bash][12] and the command prompt
on the PC is [PowerShell][13].  You should be proficient in the shell on the
platforms that you use.

Additionally, you should become familiar with the source code control system
that you will use.  For most, this means becoming familiar with
[git][14].  Don't even think of developing without using source control.

#### Cloud Services

You will need an Azure account to complete most of the tutorials in this book.
In fact, you won't be able to get very far without one. If you have an MSDN
account, you already have access to free Azure resources.  You just need to log
into your [MSDN account][15] and activate your Azure benefit.  Students may be
able to get access to [Dreamspark][16] from school resources, but this is not
suitable for developing mobile applications.  This is because storage costs
money.  If you don't have MSDN, then there is a [free trial][17] available.  
Once the trial period ends, you can move to a Pay-As-You-Go account and continue
to use free services without incurring a charge. I'll point out when you are
going to incur charges on your Azure account, but I will be using free resources
most of the time.

Aside from Azure resources, you will want some place to store your code.  This
doesn't have to be in the cloud.  If you want to use the cloud, you can use
GitHub or Visual Studio Team Services.  Both are free to use.  GitHub provides
public repositories for free.  Visual Studio Team Services provides private
respositories for free.  Visual Studio Team Services also includes other
services that I will talk about during the course of the book, some of which may
incur cost.  I will be publishing all my samples and tutorial code on GitHub so
that you can easily download it.  You don't have to use one of these resources,
but I won't be covering other service usage.

You will need a **Developer Account** for the appropriate app store if you
intend to distribute your mobile clients or if you intend to use specific cloud
services.  Apple is specific - if you intend to use push notifications or
distribute iOS apps, then you need an [Apple Developer Account][18],
[Google Developer Account][19] and/or [Windows Store Developer Account][20].
The terms of the accounts are changed constantly, so review the current terms
when you sign up.  My recommendation is to defer signing up for these programs
until you need something they offer.

Now, let's get developing!

[1]: https://www.xamarin.com/forms
[2]: https://aka.ms/azuremobileapps
[3]: http://www.learncs.org/
[4]: http://www.asp.net/
[5]: https://developer.xamarin.com/
[6]: http://www.apple.com/shop/buy-mac/mac-mini?product=MGEQ2LL/A&step=config#
[7]: http://www.intel.com/content/www/us/en/nuc/change-the-game-with-nuc.html
[8]: https://itunes.apple.com/us/app/xcode/id497799835?mt=12
[9]: https://www.xamarin.com/platform
[10]: https://www.visualstudio.com/products/visual-studio-community-vs
[11]: https://azure.microsoft.com/en-us/downloads/
[12]: http://guide.bash.academy/
[13]: https://mva.microsoft.com/en-us/training-courses/getting-started-with-powershell-3-0-jump-start-8276
[14]: https://try.github.io/levels/1/challenges/1
[15]: https://msdn.microsoft.com/en-us/default.aspx
[16]: https://www.dreamspark.com/Product/Product.aspx?productid=99
[17]: https://azure.microsoft.com/en-us/free/
[18]: https://developer.apple.com/programs/
[19]: https://play.google.com/apps/publish/signup
[20]: https://developer.microsoft.com/en-us/store/register