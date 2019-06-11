---
layout: post
title:      "Props and State Struggles"
date:       2019-06-11 22:30:41 +0000
permalink:  props_and_state_struggles
---


The biggest struggle I had in understanding props in React was adapting to the uni-directional data flow.  In the Rails framework, there are no parent objects/models/components that contain all the properties.  In essence, Rails has a multi-directional data flow that takes a different programming mindset vs React.  However, once you understand the flow, React can be used to quickly create fast and efficient applications.  The key thing to remember with props is that they are immutable; meaning that they shouldn't be changed within the child components.

This brings us to state.  Unlike props, state is mutable.  This means that it is intended to be used with data that you expect a component to be changed.  If state isn't set within a component it is considered "stateless".  Otherwise, it is "stateful".  The majority of components within React will be stateless but setting state can be incredibly useful for forms with user inputs that will change, timers, etc.  The biggest struggle with using state is knowing when and when not to use it.  As said before, the majority of components will be stateless and over time you will better understand when it is appropriate for certain components.
