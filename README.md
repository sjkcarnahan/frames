# frames
A Coordinate Frames Library for C++ providing compile-time frame analysis and vector/attitude manipulation

In engineering, two things are considered fundamental to performing good analysis:
1) units
2) coordinate frames

In fact, in school, many engineers have experiences turning in an assignment with "the right answer" and failing the assignment for lack of clarity as to the units or coordinate frames being used. However, in both academia and industry, engineering software is written with complete disregard for these fundamentals. If this is unacceptable for homework that a student did last night, why do we accept it for software that will be used years from now on billion dollar projects?

The [mpusz/units](https://github.com/mpusz/units) library has ventured to tackle the challenge of strongly typed units in c++ and Mateusz Pusz does a great job of explaining the need for strongly typed units [in this document](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1935r0.html) and in [this video](https://www.youtube.com/watch?v=nN5ya6oNImg). The work done to define physical units in c++ will really bring us into a new era of engineering software.

However, strongly typed units do not fully satisfy the fundamentals of good engineering analysis in software. Coordinate frames are just as important. For instance, in many scenarios an engineer will define both an intertial frame and a rotating frame. They could have the same or different origins, but almost always will have different coordinate axes. In this case, some vector, X, could be defined in either frame, but the numerical values of the components of X would be different in each frame. Furthermore, if a vector, X, is defined in the inertial frame and a separate vector, Y, is defined in the rotating frame, one cannot sensible add X + Y. Rather, Y must be first converted into the inertial frame (or vice versa).

Similar to the current status of physical units in software, coordinate frames are often documented in comments. This is bad for a variety of reasons, but most strongly that the definition is not carried with the variables and often ends up outdated or wrong as the code changes.  A slightly better system is one in which a variable naming convention is used to denote the frame. For instance, the AVS Lab Basilisk framework describes position vectors with a postscript _N to denote the inertial frame or _B to denote the spacecraft body frame. Unfortunately, this doesn't restrict developers from adding inertial and body frame vectors to one another. Also, it leaves developers to do a lot of raw frame conversions rather than being able to cast vectors from one frame to another.

Previous Work: There are some existing libraries that define coordinate frames, like [Boost coordinates](https://www.boost.org/doc/libs/1_66_0/libs/geometry/doc/html/geometry/reference/cs.html). However, To the author's knowledge, none contain strong compile-time type checking or casting between frames. Other libraries exist to do coordinate frame projections. It also appears that many simulation frameworks (especially robotics) have some conception of frames but still fail to enforce strong frame-dependent types.

Finally it worth mentioning the great [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page) library for c++ as it enables clear and consise linear algebra in c++ which is imperative to engineering software.

Goals:
1) strongly typed frames
2) easy safe frame casting, prevent unsafe frame casting
3) incorporation of [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page)
4) incorporation of [mpusz/units](https://github.com/mpusz/units)
5) inclusion of right and left handed orthogonal coordinate systems, rates, and attitudes
6) inclusion of vectors, tensors, matrices, and attitude representations
7) extensability and good user experience

Inspiration:
If it isn't clear yet, this project intends to take strong inspiration from [mpusz/units](https://github.com/mpusz/units) due to that library's professionalism and expertise in implementing well-executed and practical code in a complex library related to this project. It should also help in providing compatability between the libraries as the ultimate goal to have a system that includes both strongly typed units and strongly typed coordinate frames.

If you have ideas or a lot of energy for this project, please email me at sjkcarnahan@gmail.com.
