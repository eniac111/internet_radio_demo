# mkspiffs is a build tool component
# It's not used as a runtime component in the application
# This file is here to prevent CMake errors

idf_component_register(SRCS
                    INCLUDE_DIRS ".")
