# REST API
#api 

## I. Co to jest?

**API** - Application Programming Interface. 
To kontrakt, który umożliwia komunikację pomiędzy jednym serwisem/aplikacją a drugim serwisem/aplikacją

### 1. API contract

| Request    | ->  | Response |
| ---------- | --- | -------- |
| - endpoint (URL) |     | - status code         |
| - headers  |     | - headers         |
| - body           |     | - body         |

### 2. Różnica pomiędzy metodami PUT i PATCH
Obie służą do update'u ale:
- PUT wymaga, żeby body requestu był kompletne tj. to co zmieniamy + reszta
- PATCH wystarczy, że w body requestu będzie tylko to co zmieniamy

## II. POISED - API testing strategy
- Parameters (request body)
- Output (response body, status code, headers)
- Interopability
- Security
- Errors handling
- Data

## III. Sposoby na "wyłapywanie" interesujących nas calli do API
Najprościej spytać developerów, czy dane API istnieje. Poza tym można spróbować następujących sposobów:

### 1. Kopiowanie requesta z devtoolsów
1. W aplikacji: wywołuję pożądaną akcje
2. W devtools: namierzam request który chcę skopiować -> prawy klik -> Copy as cURL
![[Pasted image 20220908140630.png]]
3. W Postman: File -> Import -> Raw text -> wklejam skopiowany request

### 2. Inwestygowanie kodu źródłowego aplikacji

np.buttona 'Add to Cart', który jest wewn. elementu `<form>`. Element `<form>` może mieć wszystko, co potrzebne do stworzenia interesującego nas calla do API.

```html
<form class="product_form_ajax" enctype="multipart/form-data" action="http://store.demoqa.com/products-page/product-category/accessories/magic-mouse/" method="post" name="1">
	<div class="wpsc_product_price">
		<p class="pricedisplay specialprice 40"><span class="oldprice old_product_price_40">$200.00</span></p>
		<p class="pricedisplay normalprice 40"><span class="currentprice pricedisplay product_price_40">$150.00</span></p>
		<!-- multi currency code -->
		<span class="wpscsmall pricefloatright pricedisplay">IN: <span class="pricedisplay">$12,000.00</span></span><br>                                    															</div><!--close wpsc_product_price-->
 
		<input value="add_to_cart" name="wpsc_ajax_action" type="hidden">
		<input value="40" name="product_id" type="hidden">					
 
		<div class="wpsc_buy_button_container group">
			<div class="input-button-buy"><span><input value="Add To Cart" name="Buy" class="wpsc_buy_button" type="submit"></span>
			<div class="alert error"><p>Please select product options before adding to cart</p><span>&nbsp;</span></div>
			<div class="alert addtocart"><p>Item has been added to your cart!</p><span>&nbsp;</span></div>                                                                                                                     
		</div><!--close input-button-buy-->
	
		<div class="wpsc_loading_animation">
			<img title="Loading" alt="Loading" src="http://store.demoqa.com/wp-content/themes/mio/images/ajax-loader.gif">
		</div><!--close wpsc_loading_animation-->                                        
 
	</div><!--close wpsc_buy_button_container-->
</form>
```

1. Namierzamy element `<form>` i jego atrybuty `action` i `method`. W tym przypadku:

```html
<form action="http://store.demoqa.com/products-page/product-category/accessories/magic-mouse/" method="post">
```

2. Wewn. elementu `<form>` namierzamy elementy `<input>` i ich atrybuty `name` i `value`. W tym przypadku:

```html
<input value="add_to_cart" name="wpsc_ajax_action">
<input value="40" name="product_id">	
```

3. Konstruujemy endpointa, którego potem (w tym przypadku) wywołujemy metodą POST:

```html
<form action>?<input name>=<input value>?<input name>=<input value>
```

czyli w tym przypadku:
`http://store.demoqa.com/products-page/product-category/accessories/magic-mouse?wpsc_ajax_action=add_to_cart&product_id=40`

>https://angiejones.tech/hybrid-tests-automation-pyramid/