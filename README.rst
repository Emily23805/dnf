###############
 Dandified YUM
###############

.. image:: https://raw.githubusercontent.com/rpm-software-management/dnf/gh-pages/logos/DNF_logo.png
 
Dandified YUM (DNF) 은  `YUM <http://yum.baseurl.org/>`_ 의 업그레이드 버전입니다. 이 프로그램은  `RPM <http://rpm.org/>`_, `libsolv <https://github.com/openSUSE/libsolv>`_ 그리고 `hawkey <https://github.com/rpm-software-management/hawkey>`_ 라이브러리를 사용하여 작동합니다. 메타 데이터 처리 및 패키지 다운로드의 경우 `librepo <https://github.com/tojaj/librepo>`_ 를 사용하여 처리합니다. 컴퍼스 데이터를 효과적으로 처리하기위해  `libcomps <https://github.com/midnightercz/libcomps>`_ 를 사용합니다.

============
 설치하기
============

DNF와 모든 의존성은 Fedora 18 이상에서 사용할 수 있습니다.


선택적으로copr://rpmsoftwaremanagement/dnf-nightly에서 구할수 있는 마지막 2개의 안정적인 페도라 버전에 대한 DNF 의 야간 빌드가 있는 저장소를 사용할수 있습니다 예를 들어 아래처럼 레포지토리를 활성화 할수 있습니다.::


    dnf copr enable rpmsoftwaremanagement/dnf-nightly

그다음 dnf 를 치십시오.::

    sudo yum install dnf

In other RPM-based distributions you need to build all the components from their
sources.

======================
 소스부터 빌드해보기
======================

모든 명령어는 dnf git 디렉터리에서 실행합니다.

컴파일(빌드) 종속성 설치하는 방법::

    sudo dnf builddep dnf.spec

DNF를 컴파일하기::

    mkdir build;
    pushd build;
    cmake ..; # add '-DPYTHON_DESIRED="3"' option for Python 3 build
    make;
    popd;

DNF 를 파이썬2로 빌드하기::

    PYTHONPATH=`readlink -f .` bin/dnf-2 <arguments>

DNF 를 파이썬3로 빌드하기::

    PYTHONPATH=`readlink -f .` bin/dnf-3 <arguments>

만약 당신이 DNF 에 대한 men 페이지를 사용할려면 ``-DWITH_MAN=0`` 를 cmake 와 함께 실행시킵시오.

man 페이지 위치는 ``build/doc`` 입니다 men페이지를 읽으실려면 다음 명령어를 입력하시오. ``man -l``, 예시::

    man -l build/doc/dnf.8

=============================
 rpm 빌드 및 설치
=============================

DNF git 디렉터리에서 다음을 실행::

    $ tito build --test --rpm
    # dnf install /tmp/tito/noarch/*

===============
 작동 테스트
===============

DNF git 디렉터리에서 다음을 실행::

    mkdir build;
    pushd build;
    cmake .. && make ARGS="-V" test;
    popd;

==============
 Contribution
==============

Here's the most direct way to get your work merged into the project.

1. Fork the project
#. Clone down your fork
#. Implement your feature or bug fix and commit changes
#. If you reported a bug or you know it fixes existing bug at `Red Hat bugzilla <https://bugzilla.redhat.com/>`_, append ``(RhBug:<bug_id>)`` to your commit message
#. In special commit add your name and email under ``DNF CONTRIBUTORS`` section in `authors file <https://github.com/rpm-software-management/dnf/blob/master/AUTHORS>`_ as a reward for your generosity
#. Push the branch up to your fork
#. Send a pull request for your branch

Please, do not create the pull requests with translation (.po) files improvements. Fix the translation on `Zanata <https://fedora.zanata.org/iteration/view/dnf/master>`_ instead.

===============
 Documentation
===============

The DNF package distribution contains man pages, dnf(8) and dnf.conf(8). It is also possible to `read the DNF documentation <http://dnf.readthedocs.org>`_ online, the page includes API documentation. There's also a `wiki <https://github.com/rpm-software-management/dnf/wiki>`_ meant for contributors to DNF and related projects.

====================
 Bug reporting etc.
====================

Please report discovered bugs to the `Red Hat bugzilla <https://bugzilla.redhat.com/>`_ following this `guide <https://github.com/rpm-software-management/dnf/wiki/Bug-Reporting>`_. If you planned to propose the patch in the report, consider `Contribution`_ instead.

Freenode's irc channel ``#yum`` is meant for discussions related to both YUM and DNF. Questions should be asked there, issues discussed. Remember: ``#yum`` is not a support channel and prior research is expected from the questioner.
