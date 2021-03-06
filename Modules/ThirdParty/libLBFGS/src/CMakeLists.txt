ADD_LIBRARY( itklbfgs
  lbfgs.c
)

if( ITK_COMPILER_SUPPORTS_SSE2_32 OR
    ITK_COMPILER_SUPPORTS_SSE2_64)
  add_definitions( -DUSE_SSE  )
endif()

IF(ITK_LIBRARY_PROPERTIES)
  SET_TARGET_PROPERTIES(itklbfgs PROPERTIES ${ITK_LIBRARY_PROPERTIES})
ENDIF(ITK_LIBRARY_PROPERTIES)

set(ITK3P_INSTALL_EXPORT_NAME "${ITKLIBLBFGS-targets}")
set(ITK3P_INSTALL_INCLUDE_DIR "${ITKLIBLBFGS_INSTALL_INCLUDE_DIR}")
set(ITK3P_INSTALL_RUNTIME_DIR "${ITKLIBLBFGS_INSTALL_RUNTIME_DIR}")
set(ITK3P_INSTALL_LIBRARY_DIR "${ITKLIBLBFGS_INSTALL_LIBRARY_DIR}")
set(ITK3P_INSTALL_ARCHIVE_DIR "${ITKLIBLBFGS_INSTALL_ARCHIVE_DIR}")

INSTALL(TARGETS itklbfgs
  EXPORT ${ITK3P_INSTALL_EXPORT_NAME}
  RUNTIME DESTINATION ${ITK3P_INSTALL_RUNTIME_DIR} COMPONENT RuntimeLibraries
  LIBRARY DESTINATION ${ITK3P_INSTALL_LIBRARY_DIR} COMPONENT RuntimeLibraries
  ARCHIVE DESTINATION ${ITK3P_INSTALL_ARCHIVE_DIR} COMPONENT Development)

itk_module_target(itklbfgs NO_INSTALL)
