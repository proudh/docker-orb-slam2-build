# Docker ORB_SLAM2 Build

Build [ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2) in a Docker container starting from Ubuntu 14.04.

##To build from Docker Hub
Pull the [image](https://hub.docker.com/r/proudh/docker-orb-slam2-build/) from Docker Hub like so:
```
$ docker pull proudh/docker-orb-slam2-build
```
After doing this, go ahead and skip to running the Docker container.


##To build manually
This assumes that you are in the same directory as the Dockerfile included in this repository.
Use the following to build a Docker image with this Dockerfile with the name `proudh/docker-orb-slam2-build`:
```
$ docker build -t proudh/docker-orb-slam2-build .
```


##To run
This assumes that you are in the directory `~/docker/` with the ORB_SLAM2 repository cloned inside of this repository.
The Docker image will mount `~/docker/ORB_SLAM2` on your local machine to `/ORB_SLAM2` so that the compiled files can be retrieved there after the container is killed.
Run the following on the command line:
```
$ docker run -v ~/docker/ORB_SLAM2/:/ORB_SLAM2/ -w=/ORB_SLAM2/ proudh/docker-orb-slam2-build /bin/bash -c ./build.sh
```
This will run the build script from ORB_SLAM2 in the container.


##The struggle
Attempting to build ORB_SLAM2 in this way ends up dying here:

```
$ docker run -v ~/docker/ORB_SLAM2/:/ORB_SLAM2/ -w=/ORB_SLAM2/ slam-test /bin/bash -c ./build.sh
Configuring and building Thirdparty/DBoW2 ...
-- The C compiler identification is GNU 4.8.4
-- The CXX compiler identification is GNU 4.8.4
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Configuring done
-- Generating done
-- Build files have been written to: /ORB_SLAM2/Thirdparty/DBoW2/build
Scanning dependencies of target DBoW2
[ 33%] [ 50%] [ 50%] Building CXX object CMakeFiles/DBoW2.dir/DBoW2/FORB.cpp.o
[ 83%] [ 83%] Building CXX object CMakeFiles/DBoW2.dir/DBoW2/BowVector.cpp.o
[100%] Building CXX object CMakeFiles/DBoW2.dir/DBoW2/FeatureVector.cpp.o
Building CXX object CMakeFiles/DBoW2.dir/DUtils/Random.cpp.o
Building CXX object CMakeFiles/DBoW2.dir/DBoW2/ScoringObject.cpp.o
Building CXX object CMakeFiles/DBoW2.dir/DUtils/Timestamp.cpp.o
Linking CXX shared library ../lib/libDBoW2.so
[100%] Built target DBoW2
Configuring and building Thirdparty/g2o ...
-- The C compiler identification is GNU 4.8.4
-- The CXX compiler identification is GNU 4.8.4
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- BUILD TYPE:Release
-- Compiling on Unix
-- Try OpenMP C flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Try OpenMP CXX flag = [-fopenmp]
-- Performing Test OpenMP_FLAG_DETECTED
-- Performing Test OpenMP_FLAG_DETECTED - Success
-- Found OpenMP: -fopenmp  
-- Found Eigen3: /usr/include/eigen (Required is at least version "3.1.0") 
-- Configuring done
-- Generating done
-- Build files have been written to: /ORB_SLAM2/Thirdparty/g2o/build
Scanning dependencies of target g2o
[  3%] Building CXX object CMakeFiles/g2o.dir/g2o/types/types_sba.cpp.o
[  6%] [ 10%] [ 17%] [ 17%] Building CXX object CMakeFiles/g2o.dir/g2o/types/types_six_dof_expmap.cpp.o
[ 20%] Building CXX object CMakeFiles/g2o.dir/g2o/types/types_seven_dof_expmap.cpp.o
[ 24%] Building CXX object CMakeFiles/g2o.dir/g2o/core/hyper_graph_action.cpp.o
[ 27%] Building CXX object CMakeFiles/g2o.dir/g2o/core/hyper_graph.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/marginal_covariance_cholesky.cpp.o
[ 31%] Building CXX object CMakeFiles/g2o.dir/g2o/core/batch_stats.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/matrix_structure.cpp.o
[ 34%] [ 37%] Building CXX object CMakeFiles/g2o.dir/g2o/core/parameter.cpp.o
[ 41%] Building CXX object CMakeFiles/g2o.dir/g2o/core/cache.cpp.o
[ 48%] [ 48%] [ 51%] Building CXX object CMakeFiles/g2o.dir/g2o/core/optimizable_graph.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/solver.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/estimate_propagator.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/optimization_algorithm_factory.cpp.o
[ 55%] [ 58%] Building CXX object CMakeFiles/g2o.dir/g2o/core/factory.cpp.o
[ 62%] Building CXX object CMakeFiles/g2o.dir/g2o/core/sparse_optimizer.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/hyper_dijkstra.cpp.o
[ 68%] [ 68%] Building CXX object CMakeFiles/g2o.dir/g2o/core/parameter_container.cpp.o
[ 75%] [ 75%] Building CXX object CMakeFiles/g2o.dir/g2o/core/optimization_algorithm.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/optimization_algorithm_with_hessian.cpp.o
[ 79%] [ 82%] Building CXX object CMakeFiles/g2o.dir/g2o/core/optimization_algorithm_levenberg.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/jacobian_workspace.cpp.o
[ 86%] [ 89%] Building CXX object CMakeFiles/g2o.dir/g2o/core/robust_kernel_factory.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/robust_kernel.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/core/robust_kernel_impl.cpp.o
Building CXX object CMakeFiles/g2o.dir/g2o/stuff/timeutil.cpp.o
[ 93%] [ 96%] [100%] Building CXX object CMakeFiles/g2o.dir/g2o/stuff/string_tools.cpp.o
Building C object CMakeFiles/g2o.dir/g2o/stuff/os_specific.c.o
Building CXX object CMakeFiles/g2o.dir/g2o/stuff/property.cpp.o
c++: internal compiler error: Killed (program cc1plus)
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.8/README.Bugs> for instructions.
make[2]: *** [CMakeFiles/g2o.dir/g2o/types/types_sba.cpp.o] Error 4
make[2]: *** Waiting for unfinished jobs....
```

*To be continued...*
