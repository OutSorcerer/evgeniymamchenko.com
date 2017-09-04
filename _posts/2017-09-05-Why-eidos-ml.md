---
layout: post
title: Why eidos.ml?
---

# About eidos.ml

*This post tells what is eidos.ml and why it was created.*

[eidos.ml](https://github.com/OutSorcerer/eidos.ml) is a C# / .NET Standard library for productive development of machine learning pipelines that is based on [MathNet.Numerics](https://github.com/mathnet/mathnet-numerics).

It is inspired by [scikit-learn](https://github.com/scikit-learn/scikit-learn) but uses advantages of C# syntax and .NET runtime.

## Status

Currently library is an early development stage and suggested use-cases are participation in competitions like [Kaggle](https://www.kaggle.com/) and learning and experimenting with ML algorithms.

There **will** be breaking changes. But after the release of 1.0 it will be stable and suitable for production for small-scale problems (that fit to a single machine's memory).

# Why invent the wheel?

There are other great ML libraries for other languages and for C# too. Why create yet another?

Not only for fun.

## Why C#?

- C# today is one of the most [popular](https://www.tiobe.com/tiobe-index/), [loved and wanted](https://insights.stackoverflow.com/survey/2017#most-loved-dreaded-and-wanted) general-purpose programming languages, it has strong backing by Microsoft, enterprises and the community.

  Microsoft and others make a lot of effort to improve the language and its infrastructure and make it even more appealing.

  The set of C# features like operator overloading, LINQ, async/await, string interpolation, tuples, type deconstructors and others (and [even more](https://www.infoq.com/news/2017/06/CSharp-7.2) are coming soon), the speed how these features are released, lots of NuGet packages, great IDEs make C# one of the most pleasant languages to work with.

- Languages that are mainly used for ML (at least on Kaggle) Python, R and Julia are all dynamically typed. There is nothing bad in it but there should be a statically typed alternative.
  
  Static typing may also produce better performance and more predictable behaviour in run-time.

- Since C# is (JIT) compiled while Python and R are interpreted it has better performance. Performance is not only useful in production but also during experiments when faster code let you tune your model faster.

  While R and Python often use native libraries to boost their performance .NET Core interoperability also support that and thanks to NuGet it is convenient to ship native binaries for different platforms as part of the same NuGet package.

- With the release of .NET Core 1.0 in 2016 Microsoft finally made C# / .NET truly cross-platform and open source with free developments tools like VS Code or VS Community Edition available. That encourages its use for scientific computing.

## Why not C#?

You might ask if C# language is so good why it is not so popular for ML? I believe the main reason for that is not technical issues but the inertia of public opinion, for example a tendency to associate C# with "evil" and proprietary Microsoft (which is, in a degree, true, but it is by the same degree true for Oracle, Apple, Google or any other corporation that is *surprisingly* trying to earn money).

Moreover, by the amount of open source projects the relative position the C# community is not as good as desired, but the growth rate of C# open source is [quite good](https://octoverse.github.com/).

Considering the ML sector of open source the situation seems to be even worse than with the rest open source. It is a kind of vicious circle when people who are interested in ML even if C# is their favorite language have to use libraries other languages like Python or R and later they begin to contribute to such libraries, post code samples for them, are hired by and later hire people who use languages other than C#.

So this is of course a big challenge to take part in breaking this vicious circle about open source / ML in C#, but it is also a great opportunity.
I am aware of other attempts to make similar libraries but I cannot say that they were as successful as, for example, scikit-learn.

I do not think that I am smarter or better by any means that authors of these libraries. I believe the main reason is the mentioned vicious circle, but I also hope that the situation is changing (and I will not deny a bit of NIH but as a redemption I am going to contribute to other projects too).

Is it a good time already? My current plan is to push the development for at least a year up to 1.0 version no matter how many people will be interested in the beginning (although I understand that ultimately such a library should have many contributors to be able to compete with others and I am going to do what is in my power to attract contributors).

In the end it is the amount of GitHub forks and MRs/ NuGet downloads that shows if it is a good idea or not. Practice is the criterion of truth.

In any case the code is open source so someone else could use it for their purposes. And I will, at the very least, have fun.

## Why eidos.ml?

- The name *eidos* comes from the Plato's [theory of Forms](https://en.wikipedia.org/wiki/Theory_of_forms), where it means non-physical (but substantial) forms (or ideas) representing the most accurate reality. Since machine learning models should simulate the reality as accurately as possible an *eidos* would be an ideal model. 

  As a materialist  I do not share Plato's idea that such forms *really* exist independently from matter but they definitely exist in the minds of humankind. 

- The libraries for C# typically implement much less algorithms then scikit-learn mentioned above. eidos.ml will support all major ML algorithms including deep learning (when necessary wrapping around other libraries like [xgboost](https://github.com/dmlc/xgboost) or [TensorFlow](https://github.com/tensorflow/tensorflow)).

- The performance of eidos.ml should not worse than competitors' performance.

  eidos.ml should utilize multiple CPU cores and GPU acceleration (at least by wrapping other native libraries).

  There will be reproducible benchmarks with other popular libraries. There will be also performance tests.

- Eidos is free / open source (MIT license).

  By the way, there is another C#-based ML solution called Azure ML that may be great for enterprise use but it is not free / open source that is not good for studying ML and competing on Kaggle.

- eidos.ml will be a truly object oriented ML library, that allows to create a solution of high complexity by building a data processing pipeline as a composition of standard building blocks (preprocessing, training, evaluation algorithms) and with full extensibility.

  Good objects should have some properties like [SOLID principles](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) or [immutability](http://www.yegor256.com/2014/11/20/seven-virtues-of-good-object.html). But the library should stay pragmatic and do not make user jump through the hoops when it is not necessary (so I do not share [Yegor Bugayenko's opinion](http://www.yegor256.com/2014/11/20/seven-virtues-of-good-object.html]) that static utility classes are evil).

- Scientific code tends to be the opposite to the definition of clean code. The code of Eidos should be clean, and that will be enforced both automatically and by code review. The code must be also covered by automated tests that are launched for every commit on CI server.

- eidos.ml is cross-platform since it is implemented as .NET Standard 2.0 library. In case of addition of native binaries they will be supplied for Windows, Linux and Mac and it will always remain cross-platform. Continuos integration and automated tests will enforce portability.

- It will support import/export to allow creating huge 
ensembles of models when particular models are pre-trained in a cloud and then restored saving hours or possibly days of re-training.

- It must be easy to learn, by having good documentation and samples.

- It should ultimately support automated ML like [auto-sklearn](https://github.com/automl/auto-sklearn) or [TPOT](https://github.com/rhiever/tpot).

- It must be easy to contribute (project should be easily buildable after clone on  any developer's machine without any magic).

- eidos.ml is on the early stage of development, so it is not yet very useful but if you have great ideas about architecture or implementation of such a library it is open for any ideas and contributions. Do not hesitate and just create an issue with your improvement idea / bug report, do a merge request or just comment under this post.