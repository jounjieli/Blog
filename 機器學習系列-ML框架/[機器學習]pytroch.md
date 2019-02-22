[pytorch docs](https://pytorch.org/docs/stable/index.html)
# pytorch #
## Tensor(張量) ##
[Tensor 屬性](https://pytorch.org/docs/stable/tensor_attributes.html#tensor-attributes)
pytorch和tensorflow差不多，基本上數據都以Tensor建構。
![Tensor類型](https://upload-images.jianshu.io/upload_images/13539817-920cb6072d807598.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 基本操作 ##
Python本身是一門高級語言，使用很方便，但這也意味著很多操作很低效。
實際使用中應盡量調用內建函數(buildin-function)，這些函數底層由C/C++實現，能通過執行底層優化實現高效計算。因此在平時寫代碼時，就應養成向量化的思維習慣，千萬避免對較大的tensor進行逐元素遍歷。

- tensor      
[tensor操作參考](https://pytorch.org/docs/stable/torch.html#module-torch)，基本上很多操作以及名稱都與numpy差不多，學過numpy的話應該都不是問題。
pytorch中如果後綴_的運算或操作為in-place(就地操作)，依照原tensor只修改有改變的相關的屬性且共用同一塊內存。
pytorch可以與numpy相互轉換，且轉換後共用同一塊內存，修改時會一起改變，不過存在GPU(cuda:0、cuda:1...)的資料不能轉成numpy。

![](https://upload-images.jianshu.io/upload_images/13539817-7be83aef199d8821.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-5c10880bc046c88c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-99fc5f19fc186267.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-7b721c03dbe700c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-8fbacf28f9ed3d22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-71923be6ff10f917.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-74ea4ac1b41fa40d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## backpropagation ##
這邊看一個官方代碼，這是手動實現反向傳播，但既然使用tensorflow、pytorch還要手動微分求導就太麻煩了，而pytorch使用autograd來實現自動求導。
```
# -*- coding: utf-8 -*-

import torch

dtype = torch.float
device = torch.device("cpu")
# device = torch.device("cuda:0") # Uncomment this to run on GPU

# N is batch size; D_in is input dimension;
# H is hidden dimension; D_out is output dimension.
N, D_in, H, D_out = 64, 1000, 100, 10

# Create random input and output data
x = torch.randn(N, D_in, device=device, dtype=dtype)
y = torch.randn(N, D_out, device=device, dtype=dtype)

# Randomly initialize weights
w1 = torch.randn(D_in, H, device=device, dtype=dtype)
w2 = torch.randn(H, D_out, device=device, dtype=dtype)

learning_rate = 1e-6
for t in range(500):
    # Forward pass: compute predicted y
    h = x.mm(w1)
    h_relu = h.clamp(min=0)
    y_pred = h_relu.mm(w2)

    # Compute and print loss
    loss = (y_pred - y).pow(2).sum().item()
    print(t, loss)

    # Backprop to compute gradients of w1 and w2 with respect to loss
    grad_y_pred = 2.0 * (y_pred - y)
    grad_w2 = h_relu.t().mm(grad_y_pred)
    grad_h_relu = grad_y_pred.mm(w2.t())
    grad_h = grad_h_relu.clone()
    grad_h[h < 0] = 0
    grad_w1 = x.t().mm(grad_h)

    # Update weights using gradient descent
    w1 -= learning_rate * grad_w1
    w2 -= learning_rate * grad_w2
```

#### Computational Graphs ####
[Calculus on Computational Graphs: Backpropagation](http://colah.github.io/posts/2015-08-Backprop/)
[Tree](http://www.csie.ntnu.edu.tw/~u91029/Tree.html)
進入autograd 之前建議稍微先了解一下計算圖，如同tensorflow的Tensorboard所輸出的計算圖，但pytorch本身目前1.0是沒有支援計算圖可視化的(之後應該會新增)，不過pytorch是動態建立計算圖的，所以debug上沒有可視化也沒甚麼太大問題。
計算圖(Graph)由Tensor所構成的節點(node)所組成，沒有input的節點為leaf(葉子)，如果只有一個初始節點可以稱這個節點為root(根)，將他們連結的稱為邊(edge)。
![Tensorboard](https://upload-images.jianshu.io/upload_images/13539817-9615a1c154503ac4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![graph](https://upload-images.jianshu.io/upload_images/13539817-30f1ef5fe6ccb3a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### autograd ####
autograd 有幾個重點:
1. 當graph存在operation node(運算節點)時就會分配buffers(緩衝區)用來存取運算的intermediary(中間結果)(如$\frac{dz}{dy} = 2y = 44$，$\frac{dy}{dx} = 4x+1 = 13$，$\frac{dz}{dy} \cdot \frac{dy}{dx} = 572$...)。
然而某些運算並不需要建立buffers，ex.add、sub...。
如果f(x) = x + w那麼df/dw是1，在這種情況下，不需要建立buffers。
如果f(x) = x * w那麼df/dw是x，在這種情況下，我們需要建立buffers。
2. 當我們設置tensor的requires_grad=True時，表示這個node需要求導，它的所有衍生節點接為requires_grad=True。
3. backward執行時會以執行節點進行反向傳播運算，計算後會將derivative的值傳入requires_grad=True的leaf節點，然後將buffers的intermediary清除以節省內存。
4. ""requires_grad=True的leaf node"" 以及 ""需要被用於計算intermediary(中間結果)的node""不可以使用in-place(就地操作)。
5. with torch.no_grad:中的所有操作視為requires_grad=False，就算requires_grad設置為True依然忽略為False。
6. detach()會傳回leaf的tensor，grad_fn會等於none，is_leaf為True。

![](https://upload-images.jianshu.io/upload_images/13539817-d5d6ba981b4dc4e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 基本操作      
![](https://upload-images.jianshu.io/upload_images/13539817-0405f4d502d5c435.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-09989179cd5dc0af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-e9ea86bb2243acf5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 取得中間層grad       
![](https://upload-images.jianshu.io/upload_images/13539817-c7aaabcf7353f7ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 更新權重       
![](https://upload-images.jianshu.io/upload_images/13539817-965eb52f5f109ffc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-4b1b0592ac1f5f65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-7767f179d7e849c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-f4541a02fd26f5b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### Extending PyTorch ####
[Extending PyTorch 官方文檔](https://pytorch.org/docs/stable/notes/extending.html#extending-pytorch)
[torch.autograd.Function](https://pytorch.org/docs/stable/autograd.html#torch.autograd.Function)

- 官方 範例1：擴展一個LinearFunction
>這邊解釋一下操作:
>$LinearFunction = y = input*weight+bias$
>$nextFunction= z = f(LinearFunction )$
>1. grad_output = dz/dy
>2. dz/dx = dz/dy * dy/dx = grad_output*dy/dx = grad_output*w
>3. dz/dw = dz/dy * dy/dw = grad_output*dy/dw = grad_output*x
>4. dz/db = dz/dy * dy/db = grad_output*1
>- saved_tensors由上下文管理器存取，saved_tensors由上下文管理器提取出來。
>- ctx.needs_input_grad作為bool tuple，表示每個輸入是否需要grad。
>- 如果第一個輸入到 forward() 的參數需要grad的話，ctx.needs_input_grad[0] = True。

```
# Inherit from Function
class LinearFunction(Function):

    # 注意: forward 與 backward 都是靜態的(@staticmethods)
    @staticmethod
    # bias is an optional(可選) argument
   #它必須接受上下文ctx作為第一個參數，後跟任意數量的參數（張量或其他類型）。
   #上下文可用於存儲張量，然後可在後向傳遞期間檢索張量。
    def forward(ctx, input, weight, bias=None):
        ctx.save_for_backward(input, weight, bias)
        output = input.mm(weight.t())
        if bias is not None:
    #unsqueeze(n維前加一個維度)，expand_as(tensor)擴展維與tensor相同形狀
            output += bias.unsqueeze(0).expand_as(output)
        return output

    # This function has only a single output, so it gets only one gradient
    @staticmethod
    #它必須接受一個上下文ctx作為第一個參數,grad_output是第2個參數
    def backward(ctx, grad_output):
        # This is a pattern that is very convenient - at the top of backward
        # unpack saved_tensors and initialize all gradients w.r.t. inputs to
        # None. Thanks to the fact that additional trailing Nones are
        # ignored, the return statement is simple even when the function has
        # optional inputs.
        input, weight, bias = ctx.saved_tensors
        grad_input = grad_weight = grad_bias = None

        # These needs_input_grad checks are optional and there only to
        # improve efficiency. If you want to make your code simpler, you can
        # skip them. Returning gradients for inputs that don't require it is
        # not an error.
        if ctx.needs_input_grad[0]:
            grad_input = grad_output.mm(weight)
        if ctx.needs_input_grad[1]:
            grad_weight = grad_output.t().mm(input)
        if bias is not None and ctx.needs_input_grad[2]:
            grad_bias = grad_output.sum(0).squeeze(0)

        return grad_input, grad_weight, grad_bias
```
- 官方 範例2：擴展一個Exp
```
class Exp(Function):
    @staticmethod
    def forward(ctx, i):
        result = i.exp()
        ctx.save_for_backward(result)
        return result
    @staticmethod
    def backward(ctx, grad_output):
        result, = ctx.saved_tensors
        return grad_output * result
```
- 官方教程 範例3：擴展一個ReLU
```
import torch


class MyReLU(torch.autograd.Function):
    """
    We can implement our own custom autograd Functions by subclassing
    torch.autograd.Function and implementing the forward and backward passes
    which operate on Tensors.
    """

    @staticmethod
    def forward(ctx, input):
        """
        In the forward pass we receive a Tensor containing the input and return
        a Tensor containing the output. ctx is a context object that can be used
        to stash information for backward computation. You can cache arbitrary
        objects for use in the backward pass using the ctx.save_for_backward method.
        """
        ctx.save_for_backward(input)
        return input.clamp(min=0)

    @staticmethod
    def backward(ctx, grad_output):
        """
        In the backward pass we receive a Tensor containing the gradient of the loss
        with respect to the output, and we need to compute the gradient of the loss
        with respect to the input.
        """
        input, = ctx.saved_tensors
        grad_input = grad_output.clone()
        grad_input[input < 0] = 0
        return grad_input


dtype = torch.float
device = torch.device("cpu")
# device = torch.device("cuda:0") # Uncomment this to run on GPU

# N is batch size; D_in is input dimension;
# H is hidden dimension; D_out is output dimension.
N, D_in, H, D_out = 64, 1000, 100, 10

# Create random Tensors to hold input and outputs.
x = torch.randn(N, D_in, device=device, dtype=dtype)
y = torch.randn(N, D_out, device=device, dtype=dtype)

# Create random Tensors for weights.
w1 = torch.randn(D_in, H, device=device, dtype=dtype, requires_grad=True)
w2 = torch.randn(H, D_out, device=device, dtype=dtype, requires_grad=True)

learning_rate = 1e-6
for t in range(500):
    # To apply our Function, we use Function.apply method. We alias this as 'relu'.
    relu = MyReLU.apply

    # Forward pass: compute predicted y using operations; we compute
    # ReLU using our custom autograd operation.
    y_pred = relu(x.mm(w1)).mm(w2)

    # Compute and print loss
    loss = (y_pred - y).pow(2).sum()
    print(t, loss.item())

    # Use autograd to compute the backward pass.
    loss.backward()

    # Update weights using gradient descent
    with torch.no_grad():
        w1 -= learning_rate * w1.grad
        w2 -= learning_rate * w2.grad

        # Manually zero the gradients after updating weights
        w1.grad.zero_()
        w2.grad.zero_()
```

