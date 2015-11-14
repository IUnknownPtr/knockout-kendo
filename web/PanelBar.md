---
layout: default
prefix: ../
widgetName: PanelBar
description: The PanelBar widget displays hierarchical data in expandable sections.
docs: http://docs.telerik.com/kendo-ui/api/web/panelbar
examples:
    - title: Basic Example
      description: This example demonstrates initializing a PanelBar widget with no additional options specified.
      view: |
        <ul data-bind="kendoPanelBar: {}">
            <li>
                <span>Test 1</span>
                <ul>
                    <li>Test 1A</li>
                    <li>Test 1B</li>
                </ul>
            </li>
            <li>
                <span>Test2</span>
                <ul>
                    <li>Test 2A</li>
                    <li>Test 2B</li>
                </ul>
            </li>
        </ul>
      js: |
         var ViewModel = function() {};
      selected: true
      id: one
    - title: Passing additional options
      description: This example demonstrates passing additional options in the data-bind attribute. The **kendoPanelItem** binding can be applied to child elements to control the behavior of individual panels.
      view: |
        <input data-bind="checked: isTwoOpen" type="checkbox" /> Open 2<br/>
        <input data-bind="checked: twoEnabled" type="checkbox" /> Enabled 2<br/>
        <input data-bind="checked: twoSelected" type="checkbox" /> Selected 2
        <hr/>
        <ul data-bind="kendoPanelBar: {}">
            <li>
                <span>Test 1</span>
                <ul>
                    <li>Test 1A</li>
                    <li>Test 1B</li>
                </ul>
            </li>
            <li data-bind="kendoPanelItem: { expanded: isTwoOpen, enabled: twoEnabled, selected: twoSelected }">
                <span>Test2</span>
                <ul>
                    <li>Test 2A</li>
                    <li>Test 2B</li>
                </ul>
            </li>
        </ul>
      js: |
        var ViewModel = function() {
            this.twoEnabled = ko.observable(true);
            this.twoSelected = ko.observable().extend({ notify: "always" });
            this.isTwoOpen = ko.observable(false);
        };
      id: two
    - title: Using global options
      description: This example demonstrates setting global options in *ko.bindingHandlers.kendoPanelBar.options*. This helps to simplify the markup for settings that can be used as a default for all instances of this widget.
      view: |
        <ul data-bind="kendoPanelBar: {}">
            <li>
                <span>Test 1</span>
                <ul>
                    <li>Test 1A</li>
                    <li>Test 1B</li>
                </ul>
            </li>
            <li>
                <span>Test2</span>
                <ul>
                    <li>Test 2A</li>
                    <li>Test 2B</li>
                </ul>
            </li>
        </ul>
      js: |
        var ViewModel = function() {};
        
        ko.bindingHandlers.kendoPanelBar.options.expandMode = "single";
      id: three
      
liveOptions:
    - name: enabled
      description: Determines if users can interact with the panel item
    - name: expanded
      description: Indicates whether the panel bar item is expanded or closed
    - name: selected
      description: Indicates whether the panel bar item is selected. *Note&#58; when selecting a different panel bar item, this will not be cleared, as there are no events raised for unselecting an item.*
    - name: widget
      description: If specified, will populate an observable with a reference to the actual widget
      
futurePlans: Exploring tighter integration with templates and dataSource to allow Knockout data binding to work inside items along with support for selecting items.
---

{% include widget.html %}