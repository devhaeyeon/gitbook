# \[JS\] javascript assign vs jquery extend

extend는 객체를 merge할 때도 사용하고, 복사를 사용할 때도 사용합니다. 

\(주로 복사를 할 때 사용합니다.\)

{% embed data="{\"url\":\"https://gomakethings.com/vanilla-javascript-version-of-jquery-extend/\",\"type\":\"link\",\"title\":\"Vanilla JavaScript version of jQuery.extend\(\)\",\"description\":\"When writing vanilla JavaScript plugins, I often need to merge a set of user options into the plugin defaults to create the settings that ultimately get applied. jQuery makes this really easy via their extend\(\) method. Fortunately, there’s an easy way to do this with native JS, too! A native JS extend\(\) function The jQuery $.extend\(\) API merges the content of subsequent objects into the first one, overriding it’s original values.\",\"icon\":{\"type\":\"icon\",\"url\":\"https://gomakethings.com/img/favicon.ico\",\"aspectRatio\":0}}" %}

{% embed data="{\"url\":\"https://www.pixelstech.net/article/1477888746-Deep-clone-of-JavaScript-object\",\"type\":\"link\",\"title\":\"Deep clone of JavaScript object\",\"description\":\"In JavaScript world, it\'s frequently seen object clone. Normally when creating a clone of an object, it\'s only the reference being cloned but not all contents. In some scenarioes, it\'s desired to clon\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.pixelstech.net/favicon.ico\",\"aspectRatio\":0}}" %}

객체를 merge 할 때 jquery에서는 extend를 사용하고 javascript에서는 assign을 한다고 한다. 

그리고 객체의 복사에는 shallow copy, deep copy가 있는데

shallow copy는 객체의 레퍼런스만 복사를 하고,

deep copy는 객체의 레퍼런스, 컨텐츠들을 복사를 합니다. 

jquery의 extend는 shallow copy를 하고

javascript의 assign은 deep copy를 합니다. 







