astyle
======

from [astyle 2.02.1](http://astyle.sourceforge.net/) http://astyle.sourceforge.net/

fixed indent of `for(auto& x : list)` in c++11

```diff
@@ -2370,9 +2370,12 @@ void ASBeautifier::parseCurrentLine(const string& line)
           tabCount += classInitializerTabs;
       }
 
-      else if (isJavaStyle() && lastLineHeader == &AS_FOR)
+      // else if (isJavaStyle() && lastLineHeader == &AS_FOR)
+      // fixed by erpingwu@gmail.com, 2013-3-15
+      else if ((isCStyle() || isJavaStyle()) && lastLineHeader == &AS_FOR)
       {
         // found a java for-each statement
+        // found a c++11 for-each statement
         // so do nothing special
       }
 
```

<http://astyle.sourceforge.net/notes.html>

`Artistic Style 2.03  (April 2013)`

`Fix C++11 standard for range-based "for" loops (3458402, 3480095)`
