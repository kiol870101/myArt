  	1.a登入，b不登入
   	  a登入用 user_id 紀錄，b不登入 判斷瀏覽器 cookie 是否有存在的uuid ，沒有的話產生一個
   	2.然後 b 在登入
	  利用 uuid 匹配 cart_id 更新為 user_id 如果user_id已經有資料就合併一起
 	3.以及  a b 都登入
  	  應該會有一支全域的購物車api ，這樣不管ab裝置做什麼動作都可以更新購物車資料
   	4.ab 都不登入
      就各自紀錄自己的uuid做購物車
      不同裝置會有不同的cookie，我認為不一定要紀錄在資料表當中，但如果有紀錄在資料表當中會是更好的
      這樣他每次進入我可以直接幫他保持登入的狀況，可以減少在沒有登入的情況下加入購物車的麻煩..

<h1>[POST] /carts </h1>
 <p>帶入資料</p>
 
	{
	    store_id
	    product_id
	    product_specification_id
	    uuid
	    // todo: two devices non login and then devices logined
     	    session_id //Session::getId();
	}

<h1>[GET]  /carts</h1>
<p>回傳資料</p>

    {
        stores: [
            cart_id
            store_id
            store_name
            items:{
                [
                    cart_item_id
                    product_category_group_title
                    product_id
                    product_title
                    product_price
                    special_price
                    amount
                    total
                    items:  {
                        [...],
                        [...],
                    }
                ],
                [item....]
            },//enditem
            coupon:{
		    id
		    title
		    designated
		    deductible
		    discount
            },
            dicount:{
                id
                title
                designated
                deductible
                discount
            }
        ],
        shipping_fee
        total
    }


<h1>[POST]  /carts/checkout</h1>
 <p>帶入資料</p>

    {
        stores: [

            cart_id
            store_id
            store_name
            items:{
                [
                    cart_item_id
                    product_category_group_title
                    product_id
                    product_title
                    product_price
                    special_price
                    amount
                    total
                    items:  {
                        [...],
                        [...],
                    }
                ],
                [item....]
            },//enditem
            coupon:{
		    coupon_id
		    coupon_title
		    designated
		    deductible
		    discount
            },
            dicount:{
                id
                title
                designated
                deductible
                discount
            }
        ],
        city,
        zone,
        [運送方式]
        note
        shipping_fee
        total
    }


<h1>[PUT] /carts/{cart_item_id}</h1>
<p>傳入資料</p>
	
 	{
	    cart_item_id
	    amount
	}
 <p>回傳資料</p>
 
	{
	   total
	   shipping_fee
	   coupon:{
		id
		title
		designated
		deductible
		discount
	    },
	    dicount:{
		id
		title
		designated
		deductible
		discount
	    }
		
	}


<h1>[DELETE] /carts/item/{cart_item_id}</h1>

 	// 針對cart_item_id
  <p>回傳資料</p>
  
  	{
	   total
	    shipping_fee
	   coupon:{
		id
		title
		designated
		deductible
		discount
	    },
	    dicount:{
		id
		title
		designated
		deductible
		discount
	    }
		
	}
	

<h1>[DELETE] /carts/{cart_id}</h1>

 	//針對store
<p>回傳資料</p>
  
  	{
	   total
	   shipping_fee
	   coupon:{
		id
		title
		designated
		deductible
		discount
	    },
	    dicount:{
		id
		title
		designated
		deductible
		discount
	    }
		
	}
