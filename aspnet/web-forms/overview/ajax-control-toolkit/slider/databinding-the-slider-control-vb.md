---
uid: web-forms/overview/ajax-control-toolkit/slider/databinding-the-slider-control-vb
title: "Databinding the Slider Control (VB) | Microsoft Docs"
author: wenz
description: "The Slider control in the AJAX Control Toolkit provides a graphical slider that can be controlled using the mouse. It is possible to bind the current positio..."
ms.author: riande
ms.date: 06/02/2008
ms.assetid: 4f3ba53f-d166-422d-b29c-403348057836
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/slider/databinding-the-slider-control-vb
msc.type: authoredcontent
---
# Databinding the Slider Control (VB)

by [Christian Wenz](https://github.com/wenz)

[Download PDF](https://download.microsoft.com/download/2/d/c/2dc10e34-6983-41d4-9c08-f78f5387d32b/slider0VB.pdf)

> The Slider control in the AJAX Control Toolkit provides a graphical slider that can be controlled using the mouse. It is possible to bind the current position of the slider to another ASP.NET control.

## Overview

The Slider control in the AJAX Control Toolkit provides a graphical slider that can be controlled using the mouse. It is possible to bind the current position of the slider to another ASP.NET control.

## Steps

In order to activate the functionality of ASP.NET AJAX and the Control Toolkit, the `ScriptManager` control must be put anywhere on the page (but within the `<form>` element):

[!code-aspx[Main](databinding-the-slider-control-vb/samples/sample1.aspx)]

Next, add two `TextBox` controls to the page. One will be transformed into a graphical slider, and the other one will hold the position of the slider.

[!code-aspx[Main](databinding-the-slider-control-vb/samples/sample2.aspx)]

The next step is already the final step. The `SliderExtender` control from the ASP.NET AJAX Control Toolkit makes a slider out of the first text box and automatically updates the second text box when the slider position changes. In order for that to work, The `SliderExtender`'s `TargetControlID` attribute must be set to the ID of the first text box; the `BoundControlID` attribute must be set to the ID of the second text box.

[!code-aspx[Main](databinding-the-slider-control-vb/samples/sample3.aspx)]

As you can see in the browser, the data binding works in both directions: entering a new value in the text box updates the slider's position. If you make the second text box read only, you may add a weak protection to the text field so that it is harder for the user to manually update the value in there.

[![Slider and text box are in sync](databinding-the-slider-control-vb/_static/image2.png)](databinding-the-slider-control-vb/_static/image1.png)

Slider and text box are in sync ([Click to view full-size image](databinding-the-slider-control-vb/_static/image3.png))

> [!div class="step-by-step"]
> [Previous](using-the-slider-control-with-auto-postback-vb.md)
