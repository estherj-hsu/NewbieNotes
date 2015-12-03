#font-face

**Reference**
 - https://css-tricks.com/snippets/css/using-font-face/

    // define a custom font
    @font-face {
      font-family: myFont;
      src: url(sansation_light.woff);
    }
    
    // set different font-weight
    @font-face {
      font-family: myFont;
      src: url(sansation_bold.woff);
      font-weight: bold;
    }
    
    // Use in CSS
    body {
      font-family: myFont, sans-serif;
    }
    h1 {
      font-weight: bold;
    }


##Chinese Web Font

      //Noto Sans TC
      @import url(http://fonts.googleapis.com/earlyaccess/notosanstc.css);
      
      // cwTeXFangSong 仿宋體
      @import url(http://fonts.googleapis.com/earlyaccess/cwtexfangsong.css);
      
      // cwTeXHei 黑體
      @import url(http://fonts.googleapis.com/earlyaccess/cwtexhei.css);

      // cwTeXKai 楷體
      @import url(http://fonts.googleapis.com/earlyaccess/cwtexkai.css);
      
      // cwTeXMing 明體
      @import url(http://fonts.googleapis.com/earlyaccess/cwtexming.css);
      
      // cwTeXYen 圓體
      @import url(http://fonts.googleapis.com/earlyaccess/cwtexyen.css);
      
> Other languages: https://www.google.com/fonts/earlyaccess

##Browser Support
|  font format   |   Chrome  |  IE Edge  |  Firefox  |  Safari  | Opera
| :----: | :----: | :----: | :----: | :----: | :----: |
| TTF/OTF | 4.0 | 12.0* | 3.5 | 3.1 | 10.0 |
| WOFF | 5.0 | 12.0 | 3.6 | 5.1 | 11.1 |
| WOFF2 | 36.0 | x | 35.0* | x | 26.0 |
| SVG | 4.0 | x | x | 3.2 | 9.0 |
| EOT | x | 12.0| x | x | x |

> WOFF/WOFF2: Web Open Font Format