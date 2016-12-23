title: 'gnuplot: plot flashes and disspears'
date: 2016-12-24 00:39:46
tags: [gnuplot]
---

###### OS：openSuSE Leap-42.1

##### When I run gnuplot from the shell or a script, the resulting plot flashes by on the screen and then disappears

1. Put a pause -1 after the plot command in the file, or at the file end.
2. Use command gnuplot filename.gp - (yes, dash is the last parameter) to stay in the interactive  regime when the script completes.
3. Run gnuplot as gnuplot -persist
4. On Windows you can also use either -persist or /noend.
5. Give the persist option as part of the set terminal command.

reference: [gnuplot FAQ 7.4](http://www.gnuplot.info/faq/faq.html#x1-820007.4)