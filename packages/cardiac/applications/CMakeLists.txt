LINK_LIBRARIES(cardiac++ registration++ segmentation++ transformation++ contrib++ image++ geometry++ common++) 
IF (USE_VXL)
  LINK_LIBRARIES(irtkvnl irtkvcl irtkvnl_algo irtknetlib)
ENDIF (USE_VXL)
 
IF (BUILD_CONDOR_EXE)
  #  SET (CMAKE_CXX_COMPILER "condor_compile ${CMAKE_CXX_COMPILER}")
  # This is a hack since the line above doesn't work: this local
  # scripts executes condor_compile with the option "c++". That means,
  # the variable CMAKE_CXX_COMPILER defined in ccmake is not taken
  # into account!
  SET (CMAKE_CXX_COMPILER "${IRTK_SOURCE_DIR}/condor_compile.sh")

ELSE(BUILD_CONDOR_EXE)

  IF (BUILD_MPI_EXE)

  ELSE (BUILD_MPI_EXE)
    ADD_EXECUTABLE(bep bep.cc)
    ADD_EXECUTABLE(cardiaccrop cardiaccrop.cc)
    ADD_EXECUTABLE(cardiacphasedetection cardiacphasedetection.cc)
    ADD_EXECUTABLE(cardiacpropergation cardiacpropergation.cc)
    ADD_EXECUTABLE(cardiaccurvature cardiaccurvature.cc)
    ADD_EXECUTABLE(cardiacdof2vtk cardiacdof2vtk.cc)
    ADD_EXECUTABLE(cardiacdof2surface cardiacdof2surface.cc)
    ADD_EXECUTABLE(cardiacdotspacing cardiacdotspacing.cc)
    ADD_EXECUTABLE(cardiacimageevaluation cardiacimageevaluation.cc)
    ADD_EXECUTABLE(cardiacsurfacecompare cardiacsurfacecompare.cc)
    ADD_EXECUTABLE(cardiacsurfacemap cardiacsurfacemap.cc)
    ADD_EXECUTABLE(cardiacsurfacevolume cardiacsurfacevolume.cc)
    ADD_EXECUTABLE(cardiacvolumecount cardiacvolumecount.cc)
    ADD_EXECUTABLE(cardiacwallthickness cardiacwallthickness.cc)
    ADD_EXECUTABLE(cardiacenlargedistance cardiacenlargedistance.cc)
    ADD_EXECUTABLE(combinelandmarks combinelandmarks.cc)
    ADD_EXECUTABLE(comparebep comparebep.cc)
    ADD_EXECUTABLE(ejecfrac ejecfrac.cc)
    ADD_EXECUTABLE(featuredetect featuredetect.cc)
    ADD_EXECUTABLE(label2distancemap label2distancemap.cc)
    ADD_EXECUTABLE(late late.cc)
    ADD_EXECUTABLE(motiontrackcardiac motiontrackcardiac.cc)
    ADD_EXECUTABLE(miccai2012evaluation miccai2012evaluation.cc)
    ADD_EXECUTABLE(spatial_correct spatial_correct.cc)
    ADD_EXECUTABLE(tracktag tracktag.cc)
    ADD_EXECUTABLE(txt2cardiacvtk txt2cardiacvtk.cc)
    ADD_EXECUTABLE(Compute3DFFD Compute3DFFD.cc)

  ENDIF (BUILD_MPI_EXE)

INSTALL_TARGETS(/bin bep cardiaccrop cardiacphasedetection cardiacpropergation cardiaccurvature cardiacdof2vtk cardiacdof2surface cardiacdotspacing cardiacimageevaluation cardiacsurfacecompare cardiacsurfacemap cardiacsurfacevolume cardiacvolumecount cardiacwallthickness cardiacenlargedistance comparebep ejecfrac label2distancemap late motiontrackcardiac miccai2012evaluation spatial_correct tracktag txt2cardiacvtk Compute3DFFD) 
ENDIF (BUILD_CONDOR_EXE)

