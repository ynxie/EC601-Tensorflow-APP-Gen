## We use MobileNet 1.0_224 and MobileNet 0.5_224.  
The source of the model can be found from [here](https://github.com/googlecodelabs/tensorflow-for-poets-2)  
And the license of the model is [here](https://github.com/googlecodelabs/tensorflow-for-poets-2/blob/master/LICENSE)  
## The reason why we use MobileNet is:
* Use depth wise separable convolutions which significantly reduces the number of parameters when compared to the network with normal convolutions with the same depth in the networks
* The normal convolution is replaced by depth wise convolution followed by pointwise convolution which is called as depth wise separable convolution
* Reduce the total number of floating point multiplication operations which is favorable in mobile and embedded vision applications with less compute power
## Background Research:
* [1](https://medium.com/@yu4u/why-mobilenet-and-its-variants-e-g-shufflenet-are-fast-1c7048b9618d)
