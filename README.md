* RUNNING

java -Xbootclasspath/a:. -agentlib:heapster SimpleThread



* new_array also(!)
* sampling: 1-per-N bytes, etc.

* how to deal with garbage collection - can we get gc callbacks for
tagged objects?

* integrate google perftools

* can we call directly into native code instead of the java
back-and-forth?

* cover VMObjectAlloc also

* reentrancy

# questions

* can we modify *just* the construct for `Object`? is that possible?

# plan?


tag objects of every-n bytes allocated with stack trace.  un-attribute
those on free.  can be turned on & off arbitrarily.  eventually
restore original classes (just have to instrument once?).

so we've got 8 bytes.  we keep a maximum # of sites & objects per
site?

so, spend the first 4 bytes encoding the site, and the second 4 to a
byte count?  have a continue bit?  so, 31 bits for the size?
