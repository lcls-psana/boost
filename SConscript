#--------------------------------------------------------------------------
# File and Version Information:
#  $Id: template!SConscript! 8 2008-10-08 22:35:33Z salnikov $
#
# Description:
#  SConscript file for package nexus
#------------------------------------------------------------------------

# Do not delete following line, it must be present in
# SConscript file for any SIT project
Import('*')

from os.path import join as pjoin
from SConsTools.CondaMeta import CondaMeta
from SConsTools.standardExternalPackage import standardExternalPackage
import sys

condaBoost = CondaMeta('boost')
PREFIX = condaBoost.prefix()
INCDIR = 'include/boost'
standardExternalPackage('boost', **locals())

del INCDIR
LIBDIR = "lib"

# boost packages and their dependencies
pkgs = {'boost_chrono' : 'boost_system boost',
        'boost_date_time' : 'boost',
        'boost_filesystem' : 'boost_system boost',
        'boost_graph' : 'boost_mpi boost_regex boost',
        'boost_iostreams' : 'boost',
        'boost_math' : 'boost',
        'boost_mpi' : 'boost',
        'boost_program_options' : 'boost',
        'boost_python%d%d'%(sys.version_info.major, sys.version_info.minor) : 'boost python',
        'boost_random' : 'boost',
        'boost_regex' : 'boost',
        'boost_serialization' : 'boost',
        'boost_signals' : 'boost',
        'boost_system' : 'boost',
        'boost_thread' : 'boost',
        'boost_timer' : 'boost boost_chrono boost_system',
        'boost_unit_test_framework' : 'boost',
        'boost_wave' : 'boost_date_time boost_thread boost_filesystem boost_system boost',
        'boost_wserialization' : 'boost_serialization boost',
        }

for pkg, dep in pkgs.items():
    DEPS = dep
    PKGLIBS = pkg
    LINKLIBS = 'lib' + PKGLIBS + '*.so*'
    PKGINFO = None
    standardExternalPackage(pkg, **locals())
