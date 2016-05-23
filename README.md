# angular1.5-components

# Outputs are realized with & bindings, which function as callbacks to component events.
NOTES: two output events are register on parent html & controller. Event callback parameters name must match on child component's ctrl.onUpdate function.
For example, 'ParentComponentA' listen on on-update event propagate on 'ChildComponentB' some click action.

```javascript
ChildComponentB.js
...
ctrl.buttonClick = function(){
  ctrl.onUpdate({key1 : 'abc', key2: '123' });
}
...

ChildComponentB.html
<button ng-click="$ctrl.buttonClick">Update value - notify my parent.</button>
```

```
ParentComponentA.html
<child-component-b on-update="$ctrl.updateEventFromChild('I am just a string',key1,key2)"></child-component-b>
```
**Parent html on-update function must use `key1` and `key2` as input parameters name. Those name defined in Child controller.**

```javascript
ParentComponentA.js
...
ctrl.updateEventFromChild = function(hardCodeString, myKey1Value, myKey2Value){
  // expect(hardCodeString).toBe('I am just a string');
  // expect(myKey1Value).toBe('abc');
  // expect(myKey2Value).toBe('123');
}
...
```
**Parent html must use the same proper name defined in Child controller click function.**
