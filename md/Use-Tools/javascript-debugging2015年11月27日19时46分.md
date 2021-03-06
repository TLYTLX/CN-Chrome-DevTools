﻿# JavaScript的调试

随着JavaScript项目 **复杂性(complexity)** 的增加，开发者需要强大的调试工具，以帮助快速发现 bug 的原因，并有效地解决它。在 Chrome DevTools 中包含了许多有用的工具，以减轻开发者 **调试(debugging)** JavaScript 的痛苦。

在这一章节，我们将学习如何使用这些工具，来调试此页面上 [Google Closure hovercard demo](https://rawgit.com/google/closure-library/master/closure/goog/demos/hovercard.html) 和其他例子。

> **注意：** 如果你是一个Web开发人员，并希望得到DevTools的最新版本，您应该使用 [Chrome Canary](https://tools.google.com/dlpage/chromesxs) 。

## Sources面板[#](#sources-panel "Permalink")

 **Sources** 面板提供了调试 JavaScript 代码的功能。它提供了图形化的[V8](https://code.google.com/p/v8/) 调试器。你可以按照下面的步骤来学习 **Sources** 面板：

*   打开一个网站如 [Google Closure hovercard demo page](http://closure-library.googlecode.com/svn/trunk/closure/goog/demos/hovercard.html) 或 [TodoMVC](http://todomvc.com/examples/angularjs/) Angular 应用。
*   打开 DevTools 窗口。
*   选中 **Sources** 面板。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/javascript-debugging-overview.jpg)

 **Sources** 面板可以让你看到你所要检查的页面的所有脚本代码，并在面板选择栏下方提供了一组标准控件，提供了暂停，恢复，步进等功能。在窗口的最下方的按钮可以在遇到异常(exception)时强制暂停。源码显示在单独的标签页，通过点击 ![](https://developer.chrome.com/devtools/images/show-file-navigator.png) 打开文件导航栏，导航栏中会显示所有已打开的脚本文件。

### 执行控制[#](#execution-control "Permalink")

 **执行控制(execution control)** 按钮在侧板顶部，让你可以按步执行代码，可用的按钮有：

 **![](https://developer.chrome.com/devtools/images/continue.jpg) 继续(Continue):** 继续执行代码直到遇到下一个断点。

 **![](https://developer.chrome.com/devtools/images/step_over.jpg) 跳过(Step over):** 步进代码以查看每一行代码对变量作出的操作，当代码调用另一个函数时不会进入这个函数，使你可以专注于当前的函数。

 **![](https://developer.chrome.com/devtools/images/step_into.jpg) 跳入(Step into):** 与 Step over 类似，但是当代码调用函数时，调试器会进去这个函数并跳转到函数的第一行。

 **![](https://developer.chrome.com/devtools/images/step_out.jpg) 跳出(Step out):** 当你进入一个函数后，你可以点击 Step out 执行函数余下的代码并跳出该函数。

 **![](https://developer.chrome.com/devtools/images/disable-breakpoints.png) 断点切换(Toggle breakpoints):** 控制断点的开启和关闭，同时保持断点完好。

你还可以在 **Sources** 面板使用以下快捷键：

*   **继续(Continue)**: Mac上按下 `F8` 或 `Command` + `/` 或在其他平台按下 `Ctrl` + `/`
*   **跳过(Step over)**: Mac上按下 `F10` 或 `Command` + `'` 或在其他平台按下 `Ctrl` + `'`
*   **跳入(Step into)**: Mac上按下 `F11` 或 `Command` + `;` 或在其他平台按下 `Ctrl` + `;`
*   **跳出(Step out)**: Mac上按下 `Shift` + `F11` 或 `Shift` + `Command` + `;` 或在其他平台按下 `Shift` + `Ctrl` + `;`
*   **Next call frame**: 在所有平台按下 `Ctrl` + `.`
*   **Previous call frame**: 在所有平台按下 `Ctrl` + `,`

如果你要了解其他快捷键，参照 _[Shortcuts](https://developer.chrome.com/devtools/docs/shortcuts.html)_.

## 使用断点进行调试[#](#breakpoints "Permalink")

**断点(breakpoint)** 是在脚本中设置好的暂停处。在DevTools中使用断点可以调试JavaScript代码，DOM更新和 network calls。

### 添加和移除断点[#](#add-remove-breakpoints "Permalink")

在 **Sources** 面板打开一个JavaScript文件来调试。在下面的例子中，我们打开了 [TodoMVC](http://todomvc.com/architecture-examples/angularjs/) 的 **todoCtrl.js** 文件来进行调试。

（译者注：下图左栏中的 Sources 面板，下文有类似情况）

![](https://developer.chrome.com/devtools/docs/javascript-debugging/sources-select-todoCtrl-js.png)

点击 **边栏(line gutter)** 为当前行设置一个断点。在已经设置的断点处会有一个蓝色的标签：

![](https://developer.chrome.com/devtools/docs/javascript-debugging/sources-view-region.jpg)

你可以添加很多个断点，点击 **边栏(line gutter)** 的其他行来设置其他的断点。所有的断点可以在右侧栏的 **Breakpoints** 标签下找到。

断点可以通过侧栏中的勾选项来启用/禁用。如果断点被禁用，蓝色标签则会淡出。

在右侧栏点击断点，可以跳转到源代码中断点的所在行：

![](https://developer.chrome.com/devtools/docs/javascript-debugging/multiple-breakpoints-region.jpg)

点击**蓝色标签**来移除断点。.

右键点击**蓝色标签**打开一个菜单，菜单包含以下选项：**执行到此(Continue to Here)**， **移除断点(Remove Breakpoint)**， **编辑断点(Edit Breakpoint)**，和 **禁用断点(Disable Breakpoint)**。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/continue-to-here-region.jpg)

如果要设置一个 **条件断点(conditional breakpoint)** ，选择 **编辑断点(Edit Breakpoint)** 。
或者，也可以在 **边栏(gutter line)** 右键并选择 **添加条件断点(Add Conditional Breakpoint)** 。在输入框中，输入一个可解析为真或假的表达式。仅当条件为真时，执行会在此暂停。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/conditional-breakpoint-region.jpg)

当你在试图分析循环中的代码或者一个常被触发的事件回调函数(event callback)时，条件断点会尤其有用。

> **注意：** 在 DevTools 接口中设置断点可能不合你的心意，你也许希望从你的代码中启动调试器，你可以使用关键字 [`debugger`](console.md#setting-breakpoints-in-javascript) 来实现这一目标。


### 与断点交互(interact)[#](#breakpoints-paused "Permalink")

在你设置了一个或多个断点之后，你可以返回浏览器与你的页面交互。在下图的例子里，`removeTodo()`中有一个断点，现在任何一个在 TodoMVC app 中删除待办事项的尝试都会触发断点而暂停。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/breakpoint-paused-app.png)

要想恢复代码的执行，你可以点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键。

当脚本暂停时，你可以用右侧栏目中的 **查看表达式(Watch Expressions)**， **调用栈(Call Stack)**，和 **查看变量(Scope Variables)** 三个面板来进行交互。

#### Call Stack 面板[#](#call-stack-panel "Permalink")

The **Call Stack** 面板 displays the complete execution path that led to the point where code was paused, giving us insights into the code flaws that caused the error.

![](https://developer.chrome.com/devtools/docs/javascript-debugging/callstack-region.png)

To view the execution path including asynchronous JavaScript callbacks such as timer and XHR events, check the **Async** checkbox.

![](https://developer.chrome.com/devtools/docs/javascript-debugging/enable-async-toggle.png)

Further information and examples using async call stacks can be found in [Debugging Asynchronous JavaScript with Chrome DevTools](http://www.html5rocks.com/en/tutorials/developertools/async-call-stack/) on HTML5Rocks.com.

#### Blackbox JavaScript files[#](#blackboxing "Permalink")

When you blackbox a JavaScript source file, you will not jump into that file when stepping through code you're debugging. You are able to debug just the code you are interested in.

![](https://developer.chrome.com/devtools/docs/blackboxing-files/blackboxing-expanded.png)

You can use the Settings panel to blackbox scripts, 或 right-click in the sources panel on a file and choose Blackbox Script from the context menu.

![](https://developer.chrome.com/devtools/docs/blackboxing-files/blackboxing-dialog.png)

More information on blackboxing and how to use it can be found in the [Blackboxing JavaScript files](https://developer.chrome.com/devtools/docs/blackboxing).

#### 控制台抽屉(Console drawer)[#](#mini-console-panel "Permalink")

DevTools **控制台抽屉（console drawer）** 可以让你在目前已暂停的状态下进行试验。按 `Esc` 键打开控制台。按 `Esc` 键也可以关闭抽屉。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/console-scope-time-travel.gif)

### 动态 JavaScript 中的断点[#](#breakpoints-dynamic-javascript "Permalink")

[This is used to mark dynamicScript.js as used.](https://developer.chrome.com/devtools/docs/javascript-debugging/dynamicScript.js) <script>function loadDynamicScript() { var request = new XMLHttpRequest(); request.open('GET','https://developer.chrome.com/devtools/docs/javascript-debugging/dynamicScript.js', true); request.send(); request.onreadystatechange = function() { if (request.readyState != 4) return; eval(request.responseText); document.getElementById("dynamicScriptFunctionButton").disabled = false; document.getElementById("loadDynamicScriptButton").disabled = true; } }</script>

*   <button id="loadDynamicScriptButton" onclick="loadDynamicScript()">Load dynamic script</button>
*   在 **Sources** 面板下拉菜单中，从脚本中选择 "dynamicScript.js" ，并在line 2设置断点
*   <button id="dynamicScriptFunctionButton" onclick="dynamicScriptFunction()" disabled="">Call function from dynamic script</button>
*   你将会在断点处暂停
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/dynamic-script.jpg)

> **注意：** 注意到在文件 dynamicScript.js 最后一行的 `"//# sourceURL=dynamicScript.js"` 。 This technique gives a name to a script created with eval, 我们将在 [Source Maps](#source-maps) 章节仔细的讨论此问题。在动态 JavaScript 中，只有在用户提供了名称后，断点才可以被设定。

### 在下一个 JavaScript 声明(Statement)处暂停[#](#pause-on-next-statement "Permalink")

<script>document.addEventListener("mouseover", onMouseOver, true); function onMouseOver(event) { var target = event.target; return "onMouseOver: " + target; }</script>

*   单击 **暂停(Pause)** ![](https://developer.chrome.com/devtools/images/pause-icon.png) 按钮
*   把鼠标移动到这里
*   你会在函数 `onMouseOver` 处暂停
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/continue-to-resume.jpg)

### 在异常(Exceptions)处暂停[#](#pause-on exceptions "Permalink")

<script>function raiseAndCatchException() { var element = document.createElement("div"); try { document.body.appendChild(elemetn); } catch(e) { console.log(e); } }</script>

*   点击窗口底部的 **在异常暂停(Pause on exceptions)** ![](https://developer.chrome.com/devtools/images/pause-gray.png) 按钮button at the bottom of the window to switch to **Pause on exceptions** mode
*   Check the **Pause On Caught Exceptions** checkbox
*   <button onclick="raiseAndCatchException()">Raise exception!</button>
*   You should stop in `raiseAndCatchException` function
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/append-child.jpg)

### Pause on Uncaught Exceptions[#](#pause-on-uncaught-exceptions "Permalink")

<script>function raiseAndCatchException() { var element = document.createElement("div"); try { document.body.appendChild(elemetn); } catch(e) { console.log(e); } } function raiseException() { throw 0; }</script>

*   Click the **Pause on exceptions** ![](https://developer.chrome.com/devtools/images/pause-blue.png)button
*   Disable the **Pause On Caught Exceptions** checkbox
*   <button onclick="raiseAndCatchException()">Raise exception!</button>
*   You should not stop in raiseAndCatchException function since exception is caught
*   <button onclick="raiseException()">Raise uncaught exception!</button>
*   You should stop in `raiseException` function
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 键或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/raise-exception.jpg)

## Breakpoints on DOM Mutation Events[#](#breakpoints-mutation-events "Permalink")

<script>function appendChildButtonClicked() { var parentElement = document.getElementById("parent"); var childElement = document.createElement("div"); childElement.setAttribute("style", "border: 2px solid; padding: 5px; margin: 5px; text-align: center; width: 120px"); childElement.textContent = "Child Element"; parentElement.appendChild(childElement); }</script>

*   Right click on the "Parent Element" below and select **Inspect Element** from context menu

    <div id="parent" style="border: solid 2px; padding: 5px; margin: 5px; text-align: center; width: 140px">Parent Element</div>

*   Right click on the **Elements**' panel

    <div id="parent" ...="">element and select **Break on Subtree Modifications**</div>

*   <button onclick="appendChildButtonClicked()">Append child!</button>
*   You should stop on `appendChild` function call
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 键或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/append-child-element.jpg)

## Breakpoints on XHR[#](#breakpoints-on-xhr "Permalink")

[This is used to mark data.txt as used.](javascript-debugging/data.txt) <script>function retrieveData() { var request = new XMLHttpRequest(); request.open('GET','javascript-debugging/data.txt', true); request.send(); }</script>
*   Click the **Add** ![](https://developer.chrome.com/devtools/images/plus.png) button on **XHR Breakpoints** sidebar pane on the right side of **Sources** panel
*   Type "data.txt" in text input and hit **enter**
*   &amp;<button onclick="retrieveData()"&amp;>Retrieve data.txt by XHR&amp;</button&amp;>
*   You should stop on `send` function call
*   Right-click on the newly created breakpoint and select **Remove Breakpoint** context menu item
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/request-send.jpg)

> **Note:** To edit URL filter, double click on the XHR breakpoint entry in **XHR Breakpoints** sidebar pane. XHR breakpoint with empty URL filter will match any XHR.

## Breakpoints on JavaScript Event Listeners[#](#breakpoints-on-javascript-event-listeners "Permalink")

<script>window.addEventListener("load", onLoad, true); function onLoad() { var hovermeElement = document.getElementById("hoverme"); hovermeElement.addEventListener("mouseover", hovermeMouseOver, true); hovermeElement.addEventListener("mouseout", hovermeMouseOut, true); } function hovermeMouseOver(event) { event.target.style.backgroundColor = "grey"; } function hovermeMouseOut(event) { event.target.style.backgroundColor = "white"; }</script>
*   Expand **Event Listener Breakpoints** sidebar pane on the right side of **Scripts** panel
*   Expand **Mouse** entry
*   Set a mouseout Event Listener breakpoint by clicking on the checkbox near the **mouseout** entry

![](https://developer.chrome.com/devtools/docs/javascript-debugging/resumed.jpg)

*   Move your mouse across the box below:
*   <div id="hoverme" style="border: solid 2px; padding: 5px; margin: 5px; text-align: center; width: 100px">Hover me!</div>
*   You should stop on `mouseout` event handler
*   点击 **继续(Continue)** ![](https://developer.chrome.com/devtools/images/continue.jpg) 按钮或在 DevTools 窗口按下 `F8` 快捷键，恢复代码的执行

![](https://developer.chrome.com/devtools/docs/javascript-debugging/continue-to-resume.jpg)

> **注意：支持以下事件**  
> **键盘:** 按下(keydown)， 按键(keypress)， 松开(keyup)， 输入文字(textInput)  
> **鼠标:** 单击(click)， 双击(dblclick)， 按下(mousedown)， 松开(mouseup)， 悬停(mouseover)， 移动(mousemove)， 移开(mouseout)， 滚轮(mousewheel)  
> **控制(Control):** 调整大小(resize)， 滚动(scroll)， 缩放(zoom， 焦点(focus， 失焦(blur， 选择(select)， 改变(change)， 提交(submit)， 重置(reset)  
> **剪贴板(Clipboard):** 复制copy， 剪切(cut)， 粘贴(paste)， 复制前(beforecopy)， 剪切前(beforecut)， 粘贴前(beforepaste)  
> **载入(Load):** 载入(load)， 卸载(unload)， 中止(abort)， 错误(error)  
> **DOM 变动(DOM Mutation):** 激活(DOMActivate)， 焦点(DOMFocusIn)， 失焦(DOMFocusOut)， 属性修改(DOMAttrModified)， 字符数据修改(DOMCharacterDataModified)， 插入结点(DOMNodeInserted)， 插入结点至文档(DOMNodeInsertedIntoDocument)， 移除结点(DOMNodeRemoved)， 移除结点于文档(DOMNodeRemovedFromDocument)， 子树修改(DOMSubtreeModified， 上下文加载(DOMContentLoaded)  
> **设备(Device):** 方向(deviceorientation)， 运动(devicemotion)

</div>

<div class="collapsible">
## The Long Resume[#](#long-resume "Permalink")

暂停时，单击并按住恢复键，在恢复的同时避免 500 ms 内的所有暂停。这使半秒内的所有断点无效。使用这个功能来得到下一个事件循环，例如你可以通过这个功能避免在退出循环时不停的命中断点。

提示：当你在 DevTools 内刷新（当焦点在 DevTools 内时按下 Ctrl + R ）时，所有的暂停被禁止，直到新页面加载时开始（或直到用户按下“暂停”按钮）。但是，如果通过浏览器刷新（当焦点在 DevTools 外时按下 Ctrl + R ），任何剩余的断点将被击中。 感兴趣于页面卸载过程(unloading process)的人可以使用这个技巧。

![](https://developer.chrome.com/devtools/docs/javascript-debugging/long-resume.png)

## Live Editing[#](#liveedit "Permalink")

In **Authoring And Workflow**, we discussed how to make changes to scripts in the **Sources** panel. While at a breakpoint, it's also possible to live edit scripts by clicking into the main editor panel and making modifications.

*   Navigate to the Google Closure hovercard demo
*   In the Sources panel, open up "mouse.js" and use the Ctrl/Cmd + Shift + O to navigate to the onMouseOut() function

&amp;<div class="screenshot"&amp;>![](javascript-debugging/houseMouseOut.jpg)&amp;</div&amp;>

*   Click the **pause** button to pause debugging
*   Modify the function, adding a console.log('Moused out') to the end
*   Using the Cmd +S 或 Ctrl + S shortcuts will save these modifications. Make sure to Save As.
*   Click the **pause/resume** button to resume execution
*   When you now hover out, the new message will be logged to the console

&amp;<div class="screenshot"&amp;>![](javascript-debugging/pause-resume-mouseout.jpg)&amp;</div&amp;>

This allows you to saved changes from within the DevTools without having to leave your browser.

</div>

<div class="collapsible">
## Exceptions[#](#exceptions "Permalink")

Let's now look at how to deal with exceptions and stack traces using Chrome DevTools.  
 **Exception handling** is the process of responding to the occurrence of exceptions - exceptional situations that require special processing - often changing the normal flow of your JavaScript code's execution.

**Note:** If you are a Web Developer and want to get the latest version of DevTools, you should use [Chrome Canary](https://tools.google.com/dlpage/chromesxs).

</div>

<div class="collapsible">
## Tracking exceptions[#](#tracking-exceptions "Permalink")

When something goes wrong, you can open the DevTools console (Ctrl+Shift+J / Cmd+Option+J) and find a number of JavaScript error messages there. Each message has a link to the file name with the line number you can navigate to.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/tracking-exceptions.jpg)&amp;</div&amp;>

### Viewing exception stack trace[#](#viewing-exception-stack-trace "Permalink")

There might be several execution paths that lead to the error and it's not always obvious which one of them has happened. **Once DevTools window is opened**, exceptions in the console are accompanied with the **complete JavaScript call stacks**. You can expand these console messages to see the stack frames and navigate to the corresponding locations in the code:

&amp;<div class="screenshot"&amp;>![](javascript-debugging/exception-stack-trace.jpg)&amp;</div&amp;>

### Pause on JavaScript exceptions[#](#pause-on-exceptions "Permalink")

You may also want to pause JavaScript execution next time exception is thrown and inspect its call stack, scope variables and state of your app. A tri-state stop button ( ![](../images/pause-gray.png)) at the bottom of the Scripts panel enables you to switch between different exception handling modes: you can choose to either pause on all exception 或 only on the uncaught ones 或 you can ignore exceptions altogether.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/pause-execution.jpg)&amp;</div&amp;>

</div>

<div class="collapsible">
## Printing stack traces[#](#printing-stack-traces "Permalink")

Printing log messages to the DevTools console may be very helpful in understanding how your application behaves. You can make the log entries even more informative by including associated stack traces. There are several ways of doing that.

### Error.stack[#](#error-stack "Permalink")

Each Error object has a string property named stack that contains the stack trace:

&amp;<div class="screenshot"&amp;>![](javascript-debugging/error-stack.jpg)&amp;</div&amp;>

### console.trace()[#](#console-trace "Permalink")

You can instrument your code with console.trace() calls that would print current JavaScript call stacks:

&amp;<div class="screenshot"&amp;>![](javascript-debugging/console-trace.jpg)&amp;</div&amp;>

### console.assert()[#](#console-assert "Permalink")

There is also a way to place assertion in your JavaScript code. Just call console.assert() with the error condition as the first parameter. Whenever this expression evaluates to false you will see a corresponding console record:

&amp;<div class="screenshot"&amp;>![](javascript-debugging/console-assert.jpg)&amp;</div&amp;>

</div>

<div class="collapsible">
## Handling exceptions at runtime using window.onerror[#](#handling-exceptions-runtime "Permalink")

Chrome supports setting a handler function to window.onerror. Whenever a JavaScript exception is thrown in the window context and is not caught by any try/catch block, the function will be invoked with the exception's message, the URL of the file where the exception was thrown and the line number in that file passed as three arguments in that order. You may find it convenient to set an error handler that would collect information about uncaught exceptions and report it back to your server.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/window-onerror.jpg)&amp;</div&amp;>

</div>

<div class="collapsible">
## Pretty Print[#](#pretty-print "Permalink")

If you have trouble trying to read and debug minified JavaScript in the DevTools, a pretty printing option is available to make life easier. Here is how a minified script displayed in the tools might look prior to being displayed in the DevTools:

&amp;<div class="screenshot"&amp;>![](javascript-debugging/pretty-print-off.jpg)&amp;</div&amp;>

And by clicking on the curly brace ![](../images/prettyprint-icon.png)("Pretty Print") icon in the bottom left corner, the JavaScript is transformed into a more human readable form. This is also more easy for debugging and setting breakpoints.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/pretty-print-on.jpg)&amp;</div&amp;>

</div>

<div class="collapsible">
## Source Maps[#](#source-maps "Permalink")

Have you ever found yourself wishing you could keep your client-side code readable and more importantly debuggable even after you've combined and minified it? Well now you can through the magic of [source maps](https://docs.google.com/document/d/1U1RGAehQwRypUTovF1KRlpiOFze0b-_2gc6fAH0KY0k/edit?hl=en_US&amp;amp;pli=1&amp;amp;pli=1).

A source map is a JSON-based mapping format that creates a relationship between a minified file and its sources.

Here's an example of a simple source map:

&amp;<pre class="prettyprint"&amp;>&amp;<span class="pun"&amp;>{&amp;</span&amp;>&amp;<span class="pln"&amp;>
    version &amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="lit"&amp;>3&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="pln"&amp;>
    file&amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="str"&amp;>"out.min.js"&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="pln"&amp;>
    sourceRoot &amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="str"&amp;>""&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="pln"&amp;>
    sources&amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="pun"&amp;>[&amp;</span&amp;>&amp;<span class="str"&amp;>"foo.js"&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="str"&amp;>"bar.js"&amp;</span&amp;>&amp;<span class="pun"&amp;>],&amp;</span&amp;>&amp;<span class="pln"&amp;>
    names&amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="pun"&amp;>[&amp;</span&amp;>&amp;<span class="str"&amp;>"src"&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="str"&amp;>"maps"&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="str"&amp;>"are"&amp;</span&amp;>&amp;<span class="pun"&amp;>,&amp;</span&amp;>&amp;<span class="str"&amp;>"fun"&amp;</span&amp;>&amp;<span class="pun"&amp;>],&amp;</span&amp;>&amp;<span class="pln"&amp;>
    mappings&amp;</span&amp;>&amp;<span class="pun"&amp;>:&amp;</span&amp;>&amp;<span class="str"&amp;>"AAgBC,SAAQ,CAAEA"&amp;</span&amp;>&amp;<span class="pun"&amp;>}&amp;</span&amp;>&amp;</pre&amp;>

The idea is that when you build for production, along with minifying and combining your JavaScript files, you generate a source map that holds information about your original files. The source map causes DevTools to load your original files in addition to your minified ones. You then use the originals to set breakpoints and step through code. Meanwhile, Chrome is actually running your minified code. This gives you the illusion of running a development site in production.

### Using Source Maps[#](#using-source maps "Permalink")

**Use the Right Minifier**

You need to use a minifier that's capable of creating source maps. Closure Compiler and UglifyJS 2.0 are two such tools but there are also tools available that create source maps for CoffeeScript, SASS and many others. See the [Source maps: languages, tools and other info](https://github.com/ryanseddon/source-map/wiki/Source-maps:-languages,-tools-and-other-info) wiki page.

**Configure DevTools**

Sourcemaps are enabled by default (as of Chrome 39), but if you'd like to double-check 或 enable them, first open DevTools and click the settings cog ![gear](../images/gear.png). Under **Sources**, check **Enable JavaScript source maps**. You might also check **Enable CSS source maps** but you do not need to for this example.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/source-maps.png)&amp;</div&amp;>

**Make the Source Map Accessible**

To tell DevTools that a source map is available, verify the following line is at the end of the minified file.

`//# sourceMappingURL=/path/to/file.js.map`

This line, usually added by whatever tool generated the map, is what enables DevTools to associate minified with unminified files. In CSS, the line would look like `/*# sourceMappingURL=style.css.map */`.

If you don't want an extra comment in your file you can use an HTTP header field on the minified JavaScript file to tell DevTools where to find the source map. This requires configuration 或 customization of your web server and is beyond the scope of this document.

`X-SourceMap: /path/to/file.js.map`

Like the comment this tells DevTools where to look for the source map associated with a JavaScript file. This header also gets around the issue of referencing source maps in languages that don't support single-line comments.

You should also verify that your web server is configured to serve source maps. Some web servers, like Google App Engine for example, require explicit configuration for each file type served. In this case, your source maps should be served with a MIME type of `application/json`, but Chrome will actually [accept any content-type](http://stackoverflow.com/questions/19911929/what-mime-type-should-i-use-for-source-map-files), for example `application/octet-stream`.

Take a look at the special build of the [font dragr tool](http://dev.fontdragr.com) in Chrome, with source mapping enabled, and you'll notice that the JavaScript isn't compiled and you can see all the individual JavaScript files it references. This is using source mapping, but behind the scenes actually running the compiled code. Any errors, logs and breakpoints will map to the dev code for awesome debugging! So in effect it gives you the illusion that you're running a dev site in production.

### @sourceURL and displayName in action[#](#@sourceurl-and displayname in action "Permalink")

While not part of the source map spec the following convention allows you to make development much easier when working with evals.

This helper looks very similar to the `//# sourceMappingURL` property and is actually mentioned in the source map V3 specifications. By including the following special comment in your code, which will be evaled, you can name evals and inline scripts and styles so they appear as more logical names in your dev tools.

`//# sourceURL=source.coffee`

**Working with sourceURL**

*   Navigate to the **[demo](http://www.thecssninja.com/demo/source_mapping/compile.html)**
*   Open the DevTools and go to the **Sources** panel.
*   Enter in a filename into the _Name your code:_ input field.
*   Click on the **compile** button.
*   An alert will appear with the evaluated sum from the CoffeeScript source
*   If you expand the _Sources_ sub-panel you will now see a new file with the custom filename you entered earlier. If you double-click to view this file it will contain the compiled JavaScript for our original source. On the last line however will be a `// @sourceURL` comment indicating what the original source file was. This can greatly help with debugging when working with language abstractions.

&amp;<div class="screenshot"&amp;>![](javascript-debugging/coffeescript.jpg)&amp;</div&amp;>

#### 了解更多[#](#read-more "Permalink")

*   条件断点(Conditional breakpoints)
*   [Breakpoint actions in JavaScript](http://www.randomthink.net/blog/2012/11/breakpoint-actions-in-javascript/)
*   使用 Source Maps
*   [The Breakpoint: Source maps spectacular](https://www.youtube.com/watch?feature=player_embedded&amp;amp;v=HijZNR6kc9A)
*   [HTML5 Rocks: An Introduction To JavaScript Source maps](http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/)
*   [NetTuts: Source Maps 101](http://net.tutsplus.com/tutorials/tools-and-tips/source-maps-101/)
*   [Source maps: languages, tools and other info](https://github.com/ryanseddon/source-map/wiki/Source-maps%3A-languages%2C-tools-and-other-info)
*   [CSS Ninja: Multi-level Source maps](http://www.thecssninja.com/javascript/multi-level-sourcemaps)
*   [Source maps for CoffeeScript](http://www.coffeescriptlove.com/2012/04/source-maps-for-coffeescript.html)


Content available under the [CC-By 3.0 license](http://creativecommons.org/licenses/by/3.0/)

