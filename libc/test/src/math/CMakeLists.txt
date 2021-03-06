add_libc_testsuite(libc_math_unittests)

function(add_fp_unittest name)
  cmake_parse_arguments(
    "MATH_UNITTEST"
    "NEED_MPFR" # No optional arguments
    "" # Single value arguments
    "" # Multi-value arguments
    ${ARGN}
  )

  if(MATH_UNITTEST_NEED_MPFR)
    if(NOT LIBC_TESTS_CAN_USE_MPFR)
      message("WARNING: Math test ${name} will be skipped as MPFR library is not available.")
      return()
    endif()
  endif()

  add_libc_unittest(${name} ${MATH_UNITTEST_UNPARSED_ARGUMENTS})
  get_fq_target_name(${name} fq_target_name)
  if(MATH_UNITTEST_NEED_MPFR)
    target_link_libraries(${fq_target_name} PRIVATE libcMPFRWrapper -lmpfr -lgmp)
  endif()
  target_link_libraries(${fq_target_name} PRIVATE LibcFPTestHelpers)
endfunction(add_fp_unittest)

add_fp_unittest(
  cosf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    cosf_test.cpp
  HDRS
    sdcomp26094.h
  DEPENDS
    libc.include.errno
    libc.src.math.cosf
    libc.utils.CPP.standalone_cpp
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  sinf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    sinf_test.cpp
  HDRS
    sdcomp26094.h
  DEPENDS
    libc.include.errno
    libc.src.math.sinf
    libc.utils.CPP.standalone_cpp
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  sincosf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    sincosf_test.cpp
  HDRS
    sdcomp26094.h
  DEPENDS
    libc.include.errno
    libc.src.math.sincosf
    libc.utils.CPP.standalone_cpp
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fabs_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    fabs_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fabs
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fabsf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    fabsf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fabsf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fabsl_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    fabsl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fabsl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  trunc_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    trunc_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.trunc
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  truncf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    truncf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.truncf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  truncl_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    truncl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.truncl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  ceil_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    ceil_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.ceil
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  ceilf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    ceilf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.ceilf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  ceill_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    ceill_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.ceill
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  floor_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    floor_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.floor
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  floorf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    floorf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.floorf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  floorl_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    floorl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.floorl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  round_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    round_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.round
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  roundf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    roundf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.roundf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  roundl_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    roundl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.roundl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  expf_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    expf_test.cpp
  DEPENDS
    libc.include.errno
    libc.include.math
    libc.src.math.expf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  exp2f_test
  NEED_MPFR
  SUITE
    libc_math_unittests
  SRCS
    exp2f_test.cpp
  DEPENDS
    libc.include.errno
    libc.include.math
    libc.src.math.exp2f
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  copysign_test
  SUITE
    libc_math_unittests
  SRCS
    copysign_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.copysign
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  copysignf_test
  SUITE
    libc_math_unittests
  SRCS
    copysignf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.copysignf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  copysignl_test
  SUITE
    libc_math_unittests
  SRCS
    copysignl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.copysignl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  frexp_test
  SUITE
    libc_math_unittests
  SRCS
    frexp_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.frexp
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  frexpf_test
  SUITE
    libc_math_unittests
  SRCS
    frexpf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.frexpf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  frexpl_test
  SUITE
    libc_math_unittests
  SRCS
    frexpl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.frexpl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  logb_test
  SUITE
    libc_math_unittests
  SRCS
    logb_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.logb
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  logbf_test
  SUITE
    libc_math_unittests
  SRCS
    logbf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.logbf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  logbl_test
  SUITE
    libc_math_unittests
  SRCS
    logbl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.logbl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  modf_test
  SUITE
    libc_math_unittests
  SRCS
    modf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.modf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  modff_test
  SUITE
    libc_math_unittests
  SRCS
    modff_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.modff
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  modfl_test
  SUITE
    libc_math_unittests
  SRCS
    modfl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.modfl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fminf_test
  SUITE
    libc_math_unittests
  SRCS
    fminf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fminf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fmin_test
  SUITE
    libc_math_unittests
  SRCS
    fmin_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fmin
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fminl_test
  SUITE
    libc_math_unittests
  SRCS
    fminl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fminl
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fmaxf_test
  SUITE
    libc_math_unittests
  SRCS
    fmaxf_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fmaxf
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fmax_test
  SUITE
    libc_math_unittests
  SRCS
    fmax_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fmax
    libc.utils.FPUtil.fputil
)

add_fp_unittest(
  fmaxl_test
  SUITE
    libc_math_unittests
  SRCS
    fmaxl_test.cpp
  DEPENDS
    libc.include.math
    libc.src.math.fmaxl
    libc.utils.FPUtil.fputil
)
