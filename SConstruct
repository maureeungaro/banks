from init_env import init_environment

env = init_environment("qt5 clas12 clhep evio root geant4 xercesc mlibrary")

# library
lib_sources     = Split("""src/banks.cc""")

lbanks = env.Library(source = lib_sources, target = 'lib/banks' )

# adding tbb by hand, somehow ROOT missed this in 6.18.04
env.Append(LIBS = ['tbb'])

# Various executables

eviodump  = env.Program(source = Split("""src/evioDump.cc         src/bank_options.cc"""),            target = 'bin/evioDump' )
evio2root = env.Program(source = Split("""src/evio2root.cc src/bank_options.cc src/rootTrees.cc"""),  target = 'bin/evio2root' )

Depends(eviodump,  lbanks);
Depends(evio2root,  lbanks);
