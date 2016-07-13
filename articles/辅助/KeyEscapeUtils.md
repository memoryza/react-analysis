KeyEscapeUtils主要包含escape、unescape 用途就是将传递进去的key进行编码和解码，描述中书这样被转码+wrapper($)被用作Reactid更安全。
escape过程将

= => =0

: => =2

然后在前面$混淆了原来的key

代码如下

<code>

    'use strict';

    /**
     * Escape and wrap key so it is safe to use as a reactid
     *
     * @param {*} key to be escaped.
     * @return {string} the escaped key.
     */

    function escape(key) {
      var escapeRegex = /[=:]/g;
      var escaperLookup = {
        '=': '=0',
        ':': '=2'
      };
      var escapedString = ('' + key).replace(escapeRegex, function (match) {
        return escaperLookup[match];
      });

      return '$' + escapedString;
    }

    function unescape(key) {
      var unescapeRegex = /(=0|=2)/g;
      var unescaperLookup = {
        '=0': '=',
        '=2': ':'
      };
      var keySubstring = key[0] === '.' && key[1] === '$' ? key.substring(2) : key.substring(1);

      return ('' + keySubstring).replace(unescapeRegex, function (match) {
        return unescaperLookup[match];
      });
    }

    var KeyEscapeUtils = {
      escape: escape,
      unescape: unescape
    };
    module.exports = KeyEscapeUtils;

</code>