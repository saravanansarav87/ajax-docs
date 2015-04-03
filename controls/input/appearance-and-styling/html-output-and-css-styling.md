---
title: HTML Output and CSS Styling
page_title: HTML Output and CSS Styling | UI for ASP.NET AJAX Documentation
description: HTML Output and CSS Styling
slug: input/appearance-and-styling/html-output-and-css-styling
tags: html,output,and,css,styling
published: True
position: 4
---

# HTML Output and CSS Styling



>note Since Q1 2012 __RadInput__ has a new rendering mode for its controls -[ Single Input Rendering]({%slug input/single-input-rendering-mode%}), which is enabled by default. Therefore, this topic is no longer valid, except in the cases when __Old Rendering__ mode is activated by setting the __EnableSingleInputRendering__ property to __False__ .
>A related topic for the new rendering mode can be found[ here]({%slug input/appearance-and-styling/single-rendering-html-output%}).
>


Styles for Telerik controls are defined using Cascading Style Sheet (CSS) syntax. Each style consists of a selector that identifies an HTML element to be styled, and property/value pairs that describe each of the style specifics, e.g. color, padding, margins, etc. For example, the__.RadInput_Default__ style defines the default font and vertical alignment properties for the entire input control:

````ASPNET
	    .RadInput_Default
	    {
	         font: normal 11px Arial, Verdana, Tahoma, Sans-Serif; vertical-align: middle; 
	    }
````



See the [CSS Skin File Selectors]({%slug input/appearance-and-styling/css-skin-file-selectors%}) topic for more information on the specific CSS selectors used for __RadInput__ skins.

## HTML Output of RadDateInput

````XML
		<span class="RadInput RadInput_Default" id="RadControl1_wrapper">
			<input type="text" class="riTextBox riEnabled" id="RadControl1_text" />
			<input type="text" style="visibility: hidden" class="rdfd_" id="RadControl1" />
			<input type="hidden" id="RadControl1_ClientState" /></span>
````





````XML
		<div class="RadInput RadInput_Default" id="RadControl3_wrapper">
			<table class="riTable">
				<tbody>
					<tr>
						<td>
							<label class="riLabel">
								Label</label>
						</td>
						<td class="riCell">
							<input type="text" class="riTextBox riEnabled" id="RadControl3_text" />
							<input type="text" style="visibility: hidden" class="rdfd_" id="RadControl3" />
						</td>
						<td class="riBtn">
							<a href="#"><span>Button</span></a>
						</td>
						<td class="riSpin">
							<a href="javascript:void(0)" class="riUp"><span>Spin Up</span></a><a href="javascript:void(0)"
								class="riDown"><span>Spin Down</span></a>
						</td>
					</tr>
				</tbody>
			</table>
			<input type="hidden" id="RadControl3_ClientState" /></div>
````



The HTML output of a textbox styled by RadInputManager is the following:

````XML
		<input type="text" class="RadInputMgr RadInputMgr_Default RadInput_Enabled_Default"
			id="TextBox1" />
````



* __input.RadInputMgr.RadInputMgr_SkinName__ - the textbox has three CSS classes - one is common for all RadInputManager textboxes, one is common for all RadInputManager textboxes with a particular skin, and the last one styles the textbox according to its state (enabled, hovered, focused, invalid, etc)

__In all three examples above, the <input> element is replaced by a <textarea> element if TextMode="MultiLine".__

By default in non-single input rendering mode the width of the label is not set, and the length of the input is 100%, so it will be auto sized to get all possible free space in the table. When in single input rendering mode, the default length of the label is 40% and 60% for the input. This width can be changed with the LabelWidth property. Another reason you would might want to set EnableSingleInputRendering to false for your Telerik’s ASP.NET AJAX Input controls is to avoid re-computing of the styles dynamically on the client.

## Notes on RadInput skinning

* the RadInput table cells should have a zero padding, with the exception of the riCell table cell - it should have a right padding equal to the sum of the textbox' side borders and paddings. Otherwise the textbox will overlay the control's buttons or its right border will not be seen.

* the RadInput buttons should have a relative positioning and outline:none style in order to be clickable in Firefox. This is due to a proprietary CSS style (display:-moz-inline-stack) used to make the control behave like an inline-block element in this browser. Due to the relative positioning, Opera requires some z-index (e.g. 2). Internet Explorer 6 and 7 require the buttons to be static (not relative), otherwise a browser bug is triggered if the RadInput control is placed inside a scrollable container. In order to apply styles to IE6 and IE7 the following CSS hacks are used: "* html ..." for IE6 and "*+html ..." for IE7.



## Dynamically applied classes

The Skin CSS file includes definitions for the classes that reflect the current state of the input controls. These classes are __riEnabled__, __riDisabled__, __riEmpty__, __riFocused__, __riHover__, __riError__, and __riNegative__.

>note The various[style properties]({%slug input/appearance-and-styling/styles%})will override any of the properties set by these classes.
>
