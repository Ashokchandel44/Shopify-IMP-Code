<================================================== IMPORTANT CODE =========================================================>

<============================================= CART-DRAWER-SCRIPT ==========================================================>

<script>
$("#addToCart").click(function(event){
var id = $("#Id").val();
var qty = $("#qty").val();
event.preventDefault();
  $.ajax({
  type: 'POST',
  url: '/cart/add.js',
	cache : false,
  data: {
	quantity: $("#qty").val() ,
	id: $("#Id").val()
  },
	dataType: 'json',
   success: function (data) {
	 // $("#CartDrawer").load(location.href + " #CartDrawer");
	 // $(".cart-count-bubble").load(location.href + ".cart-count-bubble");
   $.ajax({
url: '/?section_id=cart-drawer',
type: 'GET',
dataType: 'html',
success:function(carthtml) {
$("cart-drawer.drawer").addClass("animate");
$("body.gradient").addClass("overflow-hidden");
$(".drawer").addClass("active");
if($("cart-drawer.drawer").hasClass('is-empty')){
$('cart-drawer').html($(carthtml).find('cart-drawer').html());
$("cart-drawer.is-empty .drawer__header").css("display", "block");
$("cart-drawer.is-empty .drawer__footer").css("display", "block");
$("cart-drawer.is-empty .cart__contents").css("display", "block");
$("cart-drawer.drawer").removeClass('is-empty');
$("#CartDrawer-Overlay").click(function(){
$("cart-drawer.drawer").removeClass('active');
});
} else {
//$('cart-drawer-items').html($(carthtml).find('cart-drawer-items').html());
$("cart-drawer").html($(carthtml).find('cart-drawer').html());
}
}
});
   }
   });
});
</script>

<============================================ CART-DRAWER-SCRIPT ========================================================>

<=========================================== SLICK-SLIDER-SHOPIFY =======================================================>

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick.min.js"></script>
<script>
  $(document).ready(function(){
    $('.thumbnail-list').slick({
      slidesToShow: 3,
      slidesToScroll: 1,
      vertical: true,
      verticalSwiping: true,
      arrows: true,
      prevArrow: '<button type="button" class="slick-prev">Previous</button>',
      nextArrow: '<button type="button" class="slick-next">Next</button>',
      responsive: [
        {
          breakpoint: 768,
          settings: {
          slidesToShow: 2
          }
        }
      ]
    });
  });


<============================================== SLICK-SLIDER-SHOPIFY ======================================================>

<=============================================== HOVER-MENU-SCRIPT ========================================================>

let items = document.querySelectorAll(".header__inline-menu details");
items.forEach(item => {
  let submenu = item.querySelector("ul");
  item.addEventListener("mouseenter", () => {
    item.setAttribute("open", true);
  });
  item.addEventListener("mouseleave", () => {
    setTimeout(() => {
      if (!submenu.matches(':hover')) {
        item.removeAttribute("open");
      }
    }, 300);
  });
  submenu.addEventListener("mouseenter", () => {
    item.setAttribute("open", true);
  });
  submenu.addEventListener("mouseleave", () => {
    item.removeAttribute("open");
  });
});

<=============================================== HOVER-MENU-SCRIPT =========================================================>

<============================================== CUSTOM-SLICK-SLIDER ========================================================>

<script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.9.0/slick.min.js"></script>
<link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.9.0/slick.css"/>
<link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.9.0/slick-theme.css">
<div class="thumb_slider_add">
{% for media in product.media %}
{% assign imageUrl = media.preview_image | image_url: width: 100 %}
<div>
  <img src="{{ imageUrl }}">
</div>
{% endfor %}
</div>
<div class="slick-slider_image">
  {% for media in product.media %}
    {% assign imageUrl = media.preview_image | image_url: width: 400 %}
    <div>
      <img src="{{ imageUrl }}">
    </div>
  {% endfor %}
</div>
<script>
  $('.slick-slider_image').slick({
    slidesToShow: 1,
    slidesToScroll: 1,
    arrows: true,
    fade: true,
    asNavFor: '.thumb_slider_add'
  });
  $('.thumb_slider_add').slick({
    slidesToShow: 4,
    slidesToScroll: 1,
    asNavFor: '.slick-slider_image',
    dots: false,
    centerMode: true,
    focusOnSelect: true,
    vertical: true,
    verticalSwiping: true
  });
</script>

<=============================================== CUSTOM-SLICK-SLIDER ====================================================>

<=============================================== CUSTOM-SORTING-FILTER ==================================================>

CUSTOM SORTING FITER :-
<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
<select id="sorting">
    <option>Select filter</option>
    <option value="title-ascending">Alphabetically, A-Z</option>
    <option value="title-descending">Alphabetically, Z-A</option>
    <option value="old">Oldest First</option>
    <option value="new">Newest First</option>
</select>
<script>
$(document).ready(function() {
    $('#sorting').change(function() {
        var selectedSorting = $(this).val();
        var baseUrl = 'https://quickstart-96f60939.myshopify.com/collections/all?';
        switch(selectedSorting) {
            case 'title-ascending':
            case 'title-descending':
                baseUrl += 'sort_by=' + selectedSorting;
                break;
            case 'old':
                baseUrl += 'sort_by=created-ascending&';
                break;
            case 'new':
                baseUrl += 'sort_by=created-descending&';
                break;
            default:
                break;
        }
         window.location.href = baseUrl;
    });
   var a = $(location).attr('search');
       if(a=="?sort_by=title-descending")
       {
       $('select option:nth(2)').prop("selected","selected");
       }
       else if(a=="?sort_by=title-ascending")
       {
         $('select option:nth(1)').prop("selected","selected");
       }
       else if(a=="?sort_by=created-ascending&")
       {
       $('select option:nth(3)').prop("selected","selected");
       }
       else if(a=="?sort_by=created-descending&")
       {
       $('select option:nth(4)').prop("selected","selected");
       }
       else
       {
       $('select option:nth()').prop("selected","selected");
       }
});
</script>

<================================================= CUSTOM-SORTING-FILTER =================================================>

<================================================ CUSTOM-SALES-TIMER-WORDPRESS ===========================================>

<?php
$product_id = get_the_ID();
$sales_start_date = get_post_meta($product_id, '_sale_price_dates_from', true);
$sales_end_date = get_post_meta($product_id, '_sale_price_dates_to', true);
$image = get_field('upload_sales_tag');
$heading = get_field('add_tag_heading');
$current_timestamp = current_time('timestamp');
if ($sales_start_date && $sales_end_date && $current_timestamp >= $sales_start_date && $current_timestamp <= $sales_end_date) {
    ?>
<script>
	var salesStartDate = <?php echo json_encode($sales_start_date * 1000); ?>;
	var salesEndDate = <?php echo json_encode($sales_end_date * 1000); ?>;
	var now = new Date().getTime();
	var isWithinRange = now > salesStartDate && now < salesEndDate;
	if (isWithinRange) {
		var x = setInterval(function () {
			var now = new Date().getTime();
			if (now > salesStartDate && now < salesEndDate) {
				var timeDifference = salesEndDate - now;
				var days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
				var hours = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
				var minutes = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60));
				var seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);
				document.getElementById("days").innerHTML = days + "d ";
				document.getElementById("hours").innerHTML = hours + "h ";
				document.getElementById("minutes").innerHTML = minutes + "m ";
				document.getElementById("seconds").innerHTML = seconds + "s ";
			} else {
				clearInterval(x);
				document.getElementById("countdown").innerHTML = "Sale Ended";
			}
		}, 1000);
	} else {
		document.getElementById("countdown").innerHTML = "Sale not active";
	}
</script>
    <h3 class="head"><?php echo esc_html($heading); ?></h3>
    <img src="<?php echo esc_url($image); ?>" width="200px" height="100px" alt="">
    <br>
    <div id="countdown">
    <div id="days"></div>
    <div id="hours"></div>
    <div id="minutes"></div>
    <div id="seconds"></div>
    </div><br>
    <?php
}
?>
<style>
    #countdown {
        display: flex;
    }
    #countdown div {
        margin: 0 10px;
        padding: 10px;
        background: Black;
        color: #fff;
        text-align: center;
    }
</style>


<=========================================== CUSTOM-SALES-TIMER-WORDPRESS ================================================>

<============================================= PRODUCT-GET-API-IN-CURL ===================================================>

<?php
$api_key = '17630b204a9b4ddf6e7172da79d4bfcf';
$api_secret = '023d833ee83d78035cdf2638d1b8ac3d';
$api_token = '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';
$store_name = 'quickstart-ac6ff7ae.myshopify.com';
$api_version = '2023-10';
$api_url = "https://quickstart-ac6ff7ae.myshopify.com/admin/api/2023-01/products.json";
$ch = curl_init($api_url);
$headers = array(
    'Authorization: Basic ' . base64_encode("17630b204a9b4ddf6e7172da79d4bfcf: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"),
);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
if ($response === false) {
    echo 'Curl error: ' . curl_error($ch);
} else {
    $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    if ($httpCode === 200) {
        $products = json_decode($response, true);
        echo "<table border=1 cellpadding=10px; cellspacing=0>";
        echo "<tr>";
        echo "<th>ID</th>";
        echo "<th>Title</th>";
        echo "<th>Description</th>";
        echo "<th>Photo</th>";
        echo "</tr>";
        foreach ($products['products'] as $product) {
            echo "<tr>";
            echo '<td>' . $product['id']  .'</td>';
            echo '<td>: ' . $product['title'] .'</td>';
            echo '<td>: ' . $product['body_html'] .'</td>';
            foreach ($product['images'] as $image) {
                echo '<td> <img src="' . $image['src'] . '" alt="' . $image['alt'] . '" width="auto" height="50"> </td>';
            }
            echo "</tr>";
        }
        echo "<table>";
    } else {
        echo 'HTTP error: ' . $httpCode;
    }
}
curl_close($ch);
?>

<============================================ PRODUCT-GET-API-IN-CURL ====================================================>



<!--====================================== Custom-field-code of cart page  ===============================================>
  
        <!-- this field get in cart-drawer and main-cart-items files  -->

<input  type="text" name="properties[custom-field]"><br><br>
<input type="file" id="myfile" name="properties[Additional-Image]"><br>
     
<label for="cars">Choose a car:</label>
<select id="cars" name="properties[Variant]"  form="{{ product_form_id }}">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="mercedes">Mercedes</option>
  <option value="audi">Audi</option>
</select>
<br><br>
<select class="" id="icon" name="properties[Design]" data-class="properties_design" >
		<option value="Antlers">Antlers</option>
		<option value="Arrows">Arrows</option>
</select>

<!--======================================== Custom-field-code of cart page =================================================>


<============================================ RECENTLY-Viewed-Products ======================================================>

jquery.products.min.js

(function(a){var r=a.fn.domManip,d="_tmplitem",q=/^[^<]*(<[\w\W]+>)[^>]*$|\{\{\! /,b={},f={},e,p={key:0,data:{}},h=0,c=0,l=[];function g(e,d,g,i){var c={data:i||(d?d.data:{}),_wrap:d?d._wrap:null,tmpl:null,parent:d||null,nodes:[],calls:u,nest:w,wrap:x,html:v,update:t};e&&a.extend(c,e,{nodes:[],parent:d});if(g){c.tmpl=g;c._ctnt=c._ctnt||c.tmpl(a,c);c.key=++h;(l.length?f:b)[h]=c}return c}a.each({appendTo:"append",prependTo:"prepend",insertBefore:"before",insertAfter:"after",replaceAll:"replaceWith"},function(f,d){a.fn[f]=function(n){var g=[],i=a(n),k,h,m,l,j=this.length===1&&this[0].parentNode;e=b||{};if(j&&j.nodeType===11&&j.childNodes.length===1&&i.length===1){i[d](this[0]);g=this}else{for(h=0,m=i.length;h<m;h++){c=h;k=(h>0?this.clone(true):this).get();a.fn[d].apply(a(i[h]),k);g=g.concat(k)}c=0;g=this.pushStack(g,f,i.selector)}l=e;e=null;a.tmpl.complete(l);return g}});a.fn.extend({tmpl:function(d,c,b){return a.tmpl(this[0],d,c,b)},tmplItem:function(){return a.tmplItem(this[0])},template:function(b){return a.template(b,this[0])},domManip:function(d,l,j){if(d[0]&&d[0].nodeType){var f=a.makeArray(arguments),g=d.length,i=0,h;while(i<g&&!(h=a.data(d[i++],"tmplItem")));if(g>1)f[0]=[a.makeArray(d)];if(h&&c)f[2]=function(b){a.tmpl.afterManip(this,b,j)};r.apply(this,f)}else r.apply(this,arguments);c=0;!e&&a.tmpl.complete(b);return this}});a.extend({tmpl:function(d,h,e,c){var j,k=!c;if(k){c=p;d=a.template[d]||a.template(null,d);f={}}else if(!d){d=c.tmpl;b[c.key]=c;c.nodes=[];c.wrapped&&n(c,c.wrapped);return a(i(c,null,c.tmpl(a,c)))}if(!d)return[];if(typeof h==="function")h=h.call(c||{});e&&e.wrapped&&n(e,e.wrapped);j=a.isArray(h)?a.map(h,function(a){return a?g(e,c,d,a):null}):[g(e,c,d,h)];return k?a(i(c,null,j)):j},tmplItem:function(b){var c;if(b instanceof a)b=b[0];while(b&&b.nodeType===1&&!(c=a.data(b,"tmplItem"))&&(b=b.parentNode));return c||p},template:function(c,b){if(b){if(typeof b==="string")b=o(b);else if(b instanceof a)b=b[0]||{};if(b.nodeType)b=a.data(b,"tmpl")||a.data(b,"tmpl",o(b.innerHTML));return typeof c==="string"?(a.template[c]=b):b}return c?typeof c!=="string"?a.template(null,c):a.template[c]||a.template(null,q.test(c)?c:a(c)):null},encode:function(a){return(""+a).split("<").join("&lt;").split(">").join("&gt;").split('"').join("&#34;").split("'").join("&#39;")}});a.extend(a.tmpl,{tag:{tmpl:{_default:{$2:"null"},open:"if($notnull_1){_=_.concat($item.nest($1,$2));}"},wrap:{_default:{$2:"null"},open:"$item.calls(_,$1,$2);_=[];",close:"call=$item.calls();_=call._.concat($item.wrap(call,_));"},each:{_default:{$2:"$index, $value"},open:"if($notnull_1){$.each($1a,function($2){with(this){",close:"}});}"},"if":{open:"if(($notnull_1) && $1a){",close:"}"},"else":{_default:{$1:"true"},open:"}else if(($notnull_1) && $1a){"},html:{open:"if($notnull_1){_.push($1a);}"},"=":{_default:{$1:"$data"},open:"if($notnull_1){_.push($.encode($1a));}"},"!":{open:""}},complete:function(){b={}},afterManip:function(f,b,d){var e=b.nodeType===11?a.makeArray(b.childNodes):b.nodeType===1?[b]:[];d.call(f,b);m(e);c++}});function i(e,g,f){var b,c=f?a.map(f,function(a){return typeof a==="string"?e.key?a.replace(/(<\w+)(?=[\s>])(?![^>]*_tmplitem)([^>]*)/g,"$1 "+d+'="'+e.key+'" $2'):a:i(a,e,a._ctnt)}):e;if(g)return c;c=c.join("");c.replace(/^\s*([^<\s][^<]*)?(<[\w\W]+>)([^>]*[^>\s])?\s*$/,function(f,c,e,d){b=a(e).get();m(b);if(c)b=j(c).concat(b);if(d)b=b.concat(j(d))});return b?b:j(c)}function j(c){var b=document.createElement("div");b.innerHTML=c;return a.makeArray(b.childNodes)}function o(b){return new Function("jQuery","$item","var $=jQuery,call,_=[],$data=$item.data;with($data){_.push('"+a.trim(b).replace(/([\\'])/g,"\\$1").replace(/[\r\t\n]/g," ").replace(/\$\{([^\}]*)\}/g,"{{= $1}}").replace(/\{\{(\/?)(\w+|.)(?:\(((?:[^\}]|\}(?!\}))*?)?\))?(?:\s+(.*?)?)?(\(((?:[^\}]|\}(?!\}))*?)\))?\s*\}\}/g,function(m,l,j,d,b,c,e){var i=a.tmpl.tag[j],h,f,g;if(!i)throw"Template command not found: "+j;h=i._default||[];if(c&&!/\w$/.test(b)){b+=c;c=""}if(b){b=k(b);e=e?","+k(e)+")":c?")":"";f=c?b.indexOf(".")>-1?b+c:"("+b+").call($item"+e:b;g=c?f:"(typeof("+b+")==='function'?("+b+").call($item):("+b+"))"}else g=f=h.$1||"null";d=k(d);return"');"+i[l?"close":"open"].split("$notnull_1").join(b?"typeof("+b+")!=='undefined' && ("+b+")!=null":"true").split("$1a").join(g).split("$1").join(f).split("$2").join(d?d.replace(/\s*([^\(]+)\s*(\((.*?)\))?/g,function(d,c,b,a){a=a?","+a+")":b?")":"";return a?"("+c+").call($item"+a:d}):h.$2||"")+"_.push('"})+"');}return _;")}function n(c,b){c._wrap=i(c,true,a.isArray(b)?b:[q.test(b)?b:a(b).html()]).join("")}function k(a){return a?a.replace(/\\'/g,"'").replace(/\\\\/g,"\\"):null}function s(b){var a=document.createElement("div");a.appendChild(b.cloneNode(true));return a.innerHTML}function m(o){var n="_"+c,k,j,l={},e,p,i;for(e=0,p=o.length;e<p;e++){if((k=o[e]).nodeType!==1)continue;j=k.getElementsByTagName("*");for(i=j.length-1;i>=0;i--)m(j[i]);m(k)}function m(j){var p,i=j,k,e,m;if(m=j.getAttribute(d)){while(i.parentNode&&(i=i.parentNode).nodeType===1&&!(p=i.getAttribute(d)));if(p!==m){i=i.parentNode?i.nodeType===11?0:i.getAttribute(d)||0:0;if(!(e=b[m])){e=f[m];e=g(e,b[i]||f[i],null,true);e.key=++h;b[h]=e}c&&o(m)}j.removeAttribute(d)}else if(c&&(e=a.data(j,"tmplItem"))){o(e.key);b[e.key]=e;i=a.data(j.parentNode,"tmplItem");i=i?i.key:0}if(e){k=e;while(k&&k.key!=i){k.nodes.push(j);k=k.parent}delete e._ctnt;delete e._wrap;a.data(j,"tmplItem",e)}function o(a){a=a+n;e=l[a]=l[a]||g(e,b[e.parent.key+n]||e.parent,null,true)}}}function u(a,d,c,b){if(!a)return l.pop();l.push({_:a,tmpl:d,item:this,data:c,options:b})}function w(d,c,b){return a.tmpl(a.template(d),c,b,this)}function x(b,d){var c=b.options||{};c.wrapped=d;return a.tmpl(a.template(b.tmpl),b.data,c,b.item)}function v(d,c){var b=this._wrap;return a.map(a(a.isArray(b)?b.join(""):b).filter(d||"*"),function(a){return c?a.innerText||a.textContent:a.outerHTML||s(a)})}function t(){var b=this.nodes;a.tmpl(null,null,null,this).insertBefore(b[0]);a(b).remove()}})(jQuery)


/**
 * Cookie plugin
 *
 * Copyright (c) 2006 Klaus Hartl (stilbuero.de)
 * Dual licensed under the MIT and GPL licenses:
 * http://www.opensource.org/licenses/mit-license.php
 * http://www.gnu.org/licenses/gpl.html
 *
 */
 
jQuery.cookie=function(b,j,m){if(typeof j!="undefined"){m=m||{};if(j===null){j="";m.expires=-1}var e="";if(m.expires&&(typeof m.expires=="number"||m.expires.toUTCString)){var f;if(typeof m.expires=="number"){f=new Date();f.setTime(f.getTime()+(m.expires*24*60*60*1000))}else{f=m.expires}e="; expires="+f.toUTCString()}var l=m.path?"; path="+(m.path):"";var g=m.domain?"; domain="+(m.domain):"";var a=m.secure?"; secure":"";document.cookie=[b,"=",encodeURIComponent(j),e,l,g,a].join("")}else{var d=null;if(document.cookie&&document.cookie!=""){var k=document.cookie.split(";");for(var h=0;h<k.length;h++){var c=jQuery.trim(k[h]);if(c.substring(0,b.length+1)==(b+"=")){d=decodeURIComponent(c.substring(b.length+1));break}}}return d}};

/**
 * Module to show Recently Viewed Products
 *
 * Copyright (c) 2014 Caroline Schnapp (11heavens.com)
 * Dual licensed under the MIT and GPL licenses:
 * http://www.opensource.org/licenses/mit-license.php
 * http://www.gnu.org/licenses/gpl.html
 *
 */
 
Shopify.Products=(function(){var a={howManyToShow:3,howManyToStoreInMemory:10,wrapperId:"recently-viewed-products",templateId:"recently-viewed-product-template",onComplete:null};var c=[];var h=null;var d=null;var e=0;var b={configuration:{expires:90,path:"/",domain:window.location.hostname},name:"shopify_recently_viewed",write:function(i){jQuery.cookie(this.name,i.join(" "),this.configuration)},read:function(){var i=[];var j=jQuery.cookie(this.name);if(j!==null){i=j.split(" ")}return i},destroy:function(){jQuery.cookie(this.name,null,this.configuration)},remove:function(k){var j=this.read();var i=jQuery.inArray(k,j);if(i!==-1){j.splice(i,1);this.write(j)}}};var f=function(){h.show();if(a.onComplete){try{a.onComplete()}catch(i){}}};var g=function(){if(c.length&&e<a.howManyToShow){jQuery.ajax({dataType:"json",url:"/products/"+c[0]+".js",cache:false,success:function(i){d.tmpl(i).appendTo(h);c.shift();e++;g()},error:function(){b.remove(c[0]);c.shift();g()}})}else{f()}};return{resizeImage:function(m,j){if(j==null){return m}if(j=="master"){return m.replace(/http(s)?:/,"")}var i=m.match(/\.(jpg|jpeg|gif|png|bmp|bitmap|tiff|tif)(\?v=\d+)?/i);if(i!=null){var k=m.split(i[0]);var l=i[0];return(k[0]+"_"+j+l).replace(/http(s)?:/,"")}else{return null}},showRecentlyViewed:function(i){var i=i||{};jQuery.extend(a,i);c=b.read();d=jQuery("#"+a.templateId);h=jQuery("#"+a.wrapperId);a.howManyToShow=Math.min(c.length,a.howManyToShow);if(a.howManyToShow&&d.length&&h.length){g()}},getConfig:function(){return a},clearList:function(){b.destroy()},recordRecentlyViewed:function(l){var l=l||{};jQuery.extend(a,l);var j=b.read();if(window.location.pathname.indexOf("/products/")!==-1){var k=window.location.pathname.match(/\/products\/([a-z0-9\-]+)/)[1];var i=jQuery.inArray(k,j);if(i===-1){j.unshift(k);j=j.splice(0,a.howManyToStoreInMemory)}else{j.splice(i,1);j.unshift(k)}b.write(j)}}}})();
var Shopify = Shopify || {};
// ---------------------------------------------------------------------------
// Money format handler
// ---------------------------------------------------------------------------
Shopify.money_format = "${{amount}}";
Shopify.formatMoney = function(cents, format) {
  if (typeof cents == 'string') { cents = cents.replace('.',''); }
  var value = '';
  var placeholderRegex = /\{\{\s*(\w+)\s*\}\}/;
  var formatString = (format || this.money_format);

  function defaultOption(opt, def) {
     return (typeof opt == 'undefined' ? def : opt);
  }

  function formatWithDelimiters(number, precision, thousands, decimal) {
    precision = defaultOption(precision, 2);
    thousands = defaultOption(thousands, ',');
    decimal   = defaultOption(decimal, '.');

    if (isNaN(number) || number == null) { return 0; }

    number = (number/100.0).toFixed(precision);

    var parts   = number.split('.'),
        dollars = parts[0].replace(/(\d)(?=(\d\d\d)+(?!\d))/g, '$1' + thousands),
        cents   = parts[1] ? (decimal + parts[1]) : '';

    return dollars + cents;
  }

  switch(formatString.match(placeholderRegex)[1]) {
    case 'amount':
      value = formatWithDelimiters(cents, 2);
      break;
    case 'amount_no_decimals':
      value = formatWithDelimiters(cents, 0);
      break;
    case 'amount_with_comma_separator':
      value = formatWithDelimiters(cents, 2, '.', ',');
      break;
    case 'amount_no_decimals_with_comma_separator':
      value = formatWithDelimiters(cents, 0, '.', ',');
      break;
  }

  return formatString.replace(placeholderRegex, value);
};

<============================================================================================================================>

theme.liquid

{% if template contains 'product' %}

{{ '//ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js' | script_tag }}
{{ 'jquery.products.min.js' | asset_url | script_tag }}

<script>
Shopify.Products.recordRecentlyViewed();
</script>

{% endif %}

<============================================================================================================================>

Recently-viewed-product (snippet)

{{ '//ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js' | script_tag }}
{{ 'jquery.products.min.js' | asset_url | script_tag }}

<div class="clearfix"></div>

  <div class="product-template__container page-width head-room">
        <aside class="grid">
          <div class="grid__item">
            <div id="recently-viewed-products" class="collection clearfix " >
             <header class="section-header">
              <h2 class="section-header__title border-bottom">Recently Viewed Products</h2>         
             </header>  
            </div>
          </div>
        </aside>  
  </div>
{% assign grid_item_width = 'small--one-half medium-up--one-quarter' %}
   <div class="grid grid--uniform grid--view-items leg-room">
      
      <script id="recently-viewed-product-template"  type="text/x-jquery-tmpl">
      <div class="grid__item small--one-half medium-up--one-quarter"  itemscope itemtype="http://schema.org/Product" >
      <div id="product-${handle}" class="products"}>
        <div class="image">
          <a href="${url}">
            <img src="${Shopify.Products.resizeImage(featured_image, "medium")}" />
          </a>
        </div>
        <div class="details">
          <a href="${url}">
            <span class="title">${title}</span>

            <!--Add Price Code-->
    

          </a>
        </div>
      </div>
      </div>
      </script>

      <script>
      Shopify.Products.showRecentlyViewed( { howManyToShow:8 } );
      </script>
	</div>
	
<============================================================================================================================>

{% include 'recently-viewed' %}

<============================================ RECENTLY-Viewed-Products ======================================================>

<===================================== HOW TO SETUP WP-MAIL SMTP WITH GMAIL =================================================>

USE THIS WEBSITE LINK :- https://wpforms.com/how-to-securely-send-wordpress-emails-using-gmail-smtp/

<===================================== HOW TO SETUP WP-MAIL SMTP WITH GMAIL =================================================>

<=================================== GET UNIQUE COLLECTIONS PRODUCT USING JS API ============================================>

<div id="products-container"></div>
<script>
const myHeaders = new Headers();
myHeaders.append("X-Shopify-Access-Token", "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");
myHeaders.append("Content-Type", "application/json");

const requestOptions = {
  method: "GET",
  headers: myHeaders,
  redirect: "follow"
};

fetch("https://quickstart-9ac5f6a0.myshopify.com/admin/api/2024-01/collections/457494429995/products.json", requestOptions)
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(result => {
    const productsContainer = document.getElementById('products-container');
    result.products.forEach(product => {
      const productDiv = document.createElement('div');
      productDiv.classList.add('product');
      
      productDiv.innerHTML = `
            <h2>${product.title}</h2>
            <p>${product.vendor}</p>
            <img src="${product.image.src}" alt="${product.title}" height="300px" width="auto">     
      `;
      
      productsContainer.appendChild(productDiv);
    });
  })
  .catch(error => console.error('Error:', error));
  </script>

<=================================== GET UNIQUE COLLECTIONS PRODUCT USING JS API ============================================>

<========================================= NEWSLETTER EMAIL POPUP SHOPIFY ===================================================>


<style>
.popup-letters {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    z-index: 99;
    width: 100%;
    height: 100%;
}
.popup-letters .popup-letters-inners {
    width: 31%;
    text-align: center;
    background: #fff;
    margin: auto;
    padding-bottom: 21px;
    position: absolute;
    left: 0px;
    right: 0px;
    top: 21px;
}
.popup-letters .popup-letters-inners img {
    width: 100%;
}
.popup-letters .popup-letters-inners h2 {
    text-align: left;
    margin: 0px;
    padding: 5px 10px 11px;
    color: #00CC9C;
}
.popup-letters .popup-letters-inners h3 {
    margin: 0px;
    text-align: left;
    padding: 0px 10px 11px;
}
.popup-letters .popup-letters-inners form#ContactFooter {
    max-width: 100%;
    padding: 0px 13px 0px;
}
.popup-letters .popup-letters-inners form#ContactFooter input {
    margin: 0px;
    border: solid 2px #ddd;
}
.popup-letters .popup-letters-inners form#ContactFooter label {
    color: #000;
}
.popup-letters .popup-letters-inners form#ContactFooter input {
    margin: 0px;
    border: solid 2px #ddd;
}
.popup-letters .popup-letters-inners form#ContactFooter .newsletter-form__field-wrapper button#Subscribe {
    position: static;
    background: #00CC9C;
    width: 100%;
    color: #fff;
    padding: 13px;
    font-size: 21px;
    border-radius: 9px;
    margin: 13px 0px;
}
    .popup-letters .popup-letters-inners p {
    text-align: left;
    margin: 0px;
    padding: 0px 10px 0px;
}
  .popup-letters .popup-letters-inners .newsletter-form__field-wrapper .field {
    display: inline-block;
}
    .popup-letters .popup-letters-inners .newsletter-form__field-wrapper {
    max-width: 100%;
}
    span.closs-btns {
    position: absolute;
    right: -13px;
    z-index: 999;
    width: 38px;
    height: 17px;
    top: -13px;
    cursor: pointer;
}
    @media only screen and (max-width: 767px){
      .popup-letters .popup-letters-inners {
    width: 91%;
}
      .popup-letters .popup-letters-inners form#ContactFooter {
    text-align: left;
    justify-content: left;
    align-items: baseline;
}
    }
  </style>
  
<script>
$(document).ready(function(){
  $(".closs-btns").click(function(){
	localStorage.setItem('pop_submit', 'yes');
    $(".popup-letters").css("display", "none");
  });
});
</script>

 {% if request.path == '/' %}
 <div class="popup-letters">
  <div class="popup-letters-inners">
    <span class="closs-btns"><svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path fill-rule="evenodd" clip-rule="evenodd" d="M22 12C22 17.5228 17.5228 22 12 22C6.47715 22 2 17.5228 2 12C2 6.47715 6.47715 2 12 2C17.5228 2 22 6.47715 22 12ZM8.96963 8.96965C9.26252 8.67676 9.73739 8.67676 10.0303 8.96965L12 10.9393L13.9696 8.96967C14.2625 8.67678 14.7374 8.67678 15.0303 8.96967C15.3232 9.26256 15.3232 9.73744 15.0303 10.0303L13.0606 12L15.0303 13.9696C15.3232 14.2625 15.3232 14.7374 15.0303 15.0303C14.7374 15.3232 14.2625 15.3232 13.9696 15.0303L12 13.0607L10.0303 15.0303C9.73742 15.3232 9.26254 15.3232 8.96965 15.0303C8.67676 14.7374 8.67676 14.2625 8.96965 13.9697L10.9393 12L8.96963 10.0303C8.67673 9.73742 8.67673 9.26254 8.96963 8.96965Z" fill="#FFFFFF"></path> </g></svg></span>
    <img src="https://cdn.shopify.com/s/files/1/0859/7798/9428/files/bannerss-poup.png?v=1707995248">
    <h2>You're awesome,</h2>
    <h3>Be in the Know.</h3>
    <p>sign up for new arrivals, offers and more!</p>
            {%- form 'customer', id: 'ContactFooter', class: 'footer__newsletter newsletter-form' -%}
                <div class="rodiu_btn">
                 <input type="radio" id="age1" name="contact[note][Gender]" value="Women">
                    <label for="age1">Women</label>
                    <input type="radio" id="age2" name="contact[note][Gender]" value="Men">
                    <label for="age2">Men</label><br>
                </div>
                <input type="hidden" name="contact[tags]" value="newsletter">
                <div class="newsletter-form__field-wrapper">
                  <div class="field">
                    <input
                      id="NewsletterForm--{{ section.id }}"
                      type="email"
                      name="contact[email]"
                      class="field__input"
                      value="{{ form.email }}"
                      aria-required="true"
                      autocorrect="off"
                      autocapitalize="off"
                      autocomplete="email"
                      {% if form.errors %}
                        autofocus
                        aria-invalid="true"
                        aria-describedby="ContactFooter-error"
                      {% elsif form.posted_successfully? %}
                        aria-describedby="ContactFooter-success"
                      {% endif %}
                      placeholder="Enter Your Email"
                      required
                    >
                    <label class="field__label" for="NewsletterForm--{{ section.id }}">
                      {{ 'newsletter.label' | t }}
                    </label>
                      <button
                    type="submit"
                    class="newsletter-form__button field__button"
                    name="commit"
                    id="Subscribe"
                    aria-label="{{ 'newsletter.button_label' | t }}"
                  >Sign up
                    {% comment %}{% render 'icon-arrow' %} {% endcomment %}
                  </button>
                  </div>
                  {%- if form.errors -%}
                    <small class="newsletter-form__message form__message" id="ContactFooter-error">
                      {%- render 'icon-error' -%}  <span class="exist">Email is alredy exist</span>
                      {{- form.errors.translated_fields.email | capitalize }}
                      {{ form.errors.messages.email -}}
                    </small>
                  {%- endif -%}
                </div>
              {%- endform -%}
      </div>
</div>
{% endif %}

<=================== ADD THIS SCRIPT FOR ONE TIME SHOW ===========>

<script>
 var  query_string = localStorage.getItem('pop_submit');
 if(query_string == 'yes')
 {
   $('.popup-letters').hide();
 }else{
  
	   setTimeout(function() {
	$('.popup-letters').show();
}, 9000); 
   
 }
 $(document).ready(function(){
	$('.shopify-challenge__button').click(function(){
	 console.log('set local storage');
	 localStorage.setItem('pop_submit', 'yes');
   })
 })
  </script>

<========================================= NEWSLETTER EMAIL POPUP SHOPIFY ===================================================>

