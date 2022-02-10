from init_env import init_environment

import os
ROOTSYS = os.environ['ROOTSYS']

env = init_environment("qt5 clas12 clhep evio root geant4 xercesc mlibrary hipo")
env.Append(CXXFLAGS = ' -std=c++11 ')

if env['PLATFORM'] != 'darwin':
	env.Append(RPATH = ROOTSYS + '/lib')

# library
lib_sources     = Split("""src/banks.cc""")

lbanks = env.Library(source = lib_sources, target = 'lib/banks' )

# Various executables

eviodump  = env.Program(source = Split("""src/evioDump.cc         src/bank_options.cc"""),            target = 'bin/evioDump' )
evio2root = env.Program(source = Split("""src/evio2root.cc src/bank_options.cc src/rootTrees.cc"""),  target = 'bin/evio2root' )

Depends(eviodump,  lbanks);
Depends(evio2root,  lbanks);
