if (HUMOTO_BUILD_TESTS)
    # Circular motion
    humoto_define_test(${HUMOTO_MODULE} "000" "qpOASES;config_yaml")

    #Performance test 1
    #- LexLS / qpOASES / eiQuadProg / QuadProgpp / qpmad
    #- the number of simulation runs can be specified with a command line parameter (default = 20)
    #- time is measured with different hotstarting options
    #    a) no hotstarting
    #    b) guess solution (if supported)
    #    c) guess active set (if supported)
    #    d) guess both solution and active set (if supported)
    #- measure time required for
    #    a) formulation of the preview horizon and optimization problem
    #    b) solution of the optimization problem
    #    c) the whole loop
    #- results are saved in Octave-parsable format
    humoto_define_test(${HUMOTO_MODULE} "001" "config_yaml" "lexls;qpOASES;eiquadprog;QuadProgpp;qpmad")


    # Stand still + 10 ms state shift
    humoto_define_test(${HUMOTO_MODULE} "004" "qpOASES;config_yaml")

    # testing active set handling, multiple solvers
    humoto_define_test(${HUMOTO_MODULE} "005" "qpOASES;config_yaml" "lexls")
endif()

if (HUMOTO_BUILD_REGRESSION_TESTS)
    # Circular motion
    humoto_define_regression_test(${HUMOTO_MODULE} "000" "config_yaml" "QuadProgpp;qpOASES;qpmad")

    # Active set handling
    humoto_define_regression_test(${HUMOTO_MODULE} "001" "qpOASES;config_yaml" "lexls")
endif()
