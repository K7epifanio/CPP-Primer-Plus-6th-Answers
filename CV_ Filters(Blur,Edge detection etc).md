# CV: Filters(Blur,Edge detection etc)
## How Blurs & Filters work 

* filter-low level(顏色，紋理等)，Gaussion blur, edge detction etc

### kernal convloution
*is the core of Gaussion blurs and mean blurs, sharpen, unsharpen, edge detection etc*

**Kernal** kernal is A (usually) small matrix of numbers that is used in image convolutions. 
In image processing, a kernel, convolution matrix, or mask is a small matrix. It is used for blurring, sharpening, embossing(印花), edge detection, and more. This is accomplished by doing a convolution between a kernel and an image.

ref：[Kernel (image processing) - Wikipedia](https://en.wikipedia.org/wiki/Kernel_(image_processing))

**Actually** It works by determining the value of a central pixel by adding the weighted values of all its neighbors together 

ref:[ Ludwig_ImageConvolution.ppt](http://web.pdx.edu/~jduh/courses/Archive/geog481w07/Students/Ludwig_ImageConvolution.pdf)


## finding the Edges(Sobel Operator)
### Edge detection
Edge detection is simply a case of trying to find the regions in an image where we have a sharp change in intensity or a sharp change in color, the high value means the quick change, vice verse for shallow change.  
 **sobel operator**
 该算子包含两组3x3的矩阵，分别为横向及纵向，将之与图像作平面卷积，即按所示方程式计算：
![alt text](https://wikimedia.org/api/rest_v1/media/math/render/svg/2231c7c21e974363128f9a604d8c22f49af74898)
即可分别得出横向及纵向的亮度差分近似值。如果以A代表原始图像， Gx及 Gy分别代表经横向及纵向边缘检测的图像，其公式如下：
![alt text](https://wikimedia.org/api/rest_v1/media/math/render/svg/e088749852f81ab596a87d090815b82b8d1cda70)
 x direction kernal
 y direction kernal
 图像的每一个像素的横向及纵向梯度近似值可用以下的公式结合，来计算梯度的大小。standardization 
 G=squre root(Gx2+Gy2)
 ![a7a95ae5d7d87b2a7512c276f096b42688322816](https://wikimedia.org/api/rest_v1/media/math/render/svg/a7a95ae5d7d87b2a7512c276f096b42688322816)
 然后可用以下公式计算梯度方向。
 ![2bca450dbdb972aff5c110286a76d835460ed252](https://wikimedia.org/api/rest_v1/media/math/render/svg/2bca450dbdb972aff5c110286a76d835460ed252)
 
 ref: https://zh.wikipedia.org/wiki/%E7%B4%A2%E8%B2%9D%E7%88%BE%E7%AE%97%E5%AD%90
https://medium.com/@Rifur/%E8%A8%8E%E8%AB%96%E7%B4%A2%E4%BC%AF%E7%AE%97%E5%AD%90-sobel-%E7%9A%84-convolution-%E5%95%8F%E9%A1%8C-e986ce026e72
 sobel噪声较多，因此通常先使用高斯模糊去除噪声
 
 ## Canny Edge Detector
 Canny Edge Detector使用sobel operator，去除坏的edge，保留好的edge
 _the input of canny is simply the output of sobel_
 
**canny** worsk by taking the image from the sobel output. Thinging all the edges so they  are 1 pixel wide. 因为主要任务是找到edge在哪而非显示厚度
* canny 首先find 所有的edges
* 随后使用 hysteresis(迟滞，滞后) thresholding
_实质上，我们通过比较this edge的梯度与它周围的edge，或者说比较this pixel与它周围的pixel大小，取最大的那个以获得一个最thin的edge_
 * filter的作用是保留dominate edges，去除非主要的edges
 
滞后滤波器
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 