# Project3_Lab1
软件项目研发实践（3）Lab1

选择Phone and Tablet选项卡中Empty Activity

![屏幕截图 2025-05-04 133927](https://github.com/user-attachments/assets/a0b31d19-b05c-402b-aed0-ddd5c2302e75)
![屏幕截图 2025-05-04 134032](https://github.com/user-attachments/assets/976e18cc-6a9a-43d9-bbbe-87dc209aa912)

## Compose 入门

微调界面

为Greeting 设置不同的背景色，使用Surface 包围 Text 可组合项。Surface 会采用一种颜色，因此请使用 MaterialTheme.colorScheme.primary。

![屏幕截图 2025-05-04 134320](https://github.com/user-attachments/assets/db93ada5-5fad-4c0e-839c-87e8ca75c4ab)

上述代码将嵌套在 Surface 内的组件将在该背景颜色之上绘制。

预览的效果：

![屏幕截图 2025-05-04 135138](https://github.com/user-attachments/assets/2d84d0b5-175a-4104-bbec-caa3ea08aa5e)

文字颜色更改成白色是Material 组件提供的功能，为了获得更好的UI体验。在这种情况下，Surface 会了解，当该背景设置为 primary 颜色后，其上的任何文本都应使用 onPrimary 颜色，此颜色也在主题中进行了定义。

修饰符

大多数 Compose 界面元素（例如 Surface 和 Text）都接受可选的 modifier 参数。修饰符会指示界面元素如何在其父布局中放置、显示或表现。Greeting 可组合项已有一个默认修饰符，该修饰符随后会传递给 Text。
可以试着修改 modifier 的属性，例如，padding 修饰符会在其修饰的元素周围应用一定的空间。

![屏幕截图 2025-05-04 135246](https://github.com/user-attachments/assets/131a9440-4e3f-4fa9-b62f-5d48250a2a2b)

为默认修饰符添加内边距修饰符：modifier.padding(24.dp)。形成如下效果：

![屏幕截图 2025-05-04 135335](https://github.com/user-attachments/assets/71ccfe18-0591-49ee-b811-5be1cd50e622)

重复使用可组合项
添加到界面的组件越多，创建的嵌套层级就越多。如果函数变得非常大，可能会影响可读性。通过创建可重用的小型组件，可以轻松构建应用中所用界面元素的库。每个组件对应于屏幕的一个部分，可以单独修改。
最佳实践是，函数应包含一个修饰符参数，系统默认为该参数分配空修饰符。将此修饰符转发到您在函数内调用的第一个可组合项。这样，调用点就可以在可组合函数之外调整布局指令和行为了。

创建一个MyApp 的可组合项，该组合项中包含Greeting。

![屏幕截图 2025-05-04 135501](https://github.com/user-attachments/assets/1492ac47-b425-4e34-83e2-3fa129b4b2ec)

现在可以重复使用 MyApp 可组合项，可以省去 onCreate 回调和预览，从而避免重复编写代码。

在预览中，调用 MyApp 并移除预览的名称。MainActivity.kt 的代码应如下：

![屏幕截图 2025-05-04 140239](https://github.com/user-attachments/assets/9ae60be7-a3fe-4d9b-b1a7-71b8de0bdee1)
![屏幕截图 2025-05-04 140325](https://github.com/user-attachments/assets/587a75b1-a506-4910-91c9-4be8a6b32079)
![屏幕截图 2025-05-04 140404](https://github.com/user-attachments/assets/3153bddd-4461-4d05-86ce-3fb6446eda05)

创建Compose中的列（Column）和行（Row）

Compose 中的三个基本标准布局元素是 Column、Row 和 Box 可组合项。

![屏幕截图 2025-05-04 140454](https://github.com/user-attachments/assets/5d5ed3fe-ce8e-4f4a-996e-63e8654ceb9a)
![屏幕截图 2025-05-04 140525](https://github.com/user-attachments/assets/f4536460-d514-4b8e-834b-9123c008a126)

接下来为修饰符（modifier）添加更多的属性，来查看显示效果。使用 fillMaxWidth 和 padding 修饰符复制以下布局。注意更改工程中的代码，使用以下代码修改Compose函数。

![image](https://github.com/user-attachments/assets/ef98e947-ffb4-4654-ac33-6424eb2033df)
![image](https://github.com/user-attachments/assets/a7c209ca-6b37-4bd0-b418-053776b667c3)

添加按钮

向 Greeting 添加可点击元素，因此需要先添加对应的按钮。Button 是 material3 软件包提供的一种可组合项，它采用可组合项作为最后一个参数，同时提供了多种类型，如ElevatedButton、FilledTonalButton、OutlinedButton 和 TextButton等。
由于没有 alignEnd 修饰符，因此您需要在开始时为该可组合项赋予一定的 weight。weight 修饰符会让元素填满所有可用空间，使其“具有弹性”，也就是会推开其他没有权重的元素（即“无弹性”元素）。该修饰符还会使 fillMaxWidth 修饰符变得多余。

![image](https://github.com/user-attachments/assets/6c5e4eda-1596-44b3-8b52-a8e4f12e1a64)
![image](https://github.com/user-attachments/assets/1d9a2787-06bc-415d-bcc4-5dc7a830a245)

Compose中的状态（State）

在本部分中，将向屏幕中添加一些互动。到目前为止，已经创建了一些静态布局，但现在要让它们响应用户更改。

![image](https://github.com/user-attachments/assets/ee0512bd-b469-46fe-806b-87cf20ebc771)
![image](https://github.com/user-attachments/assets/a2a10f15-0c85-4e84-b676-0a80858aa199)

