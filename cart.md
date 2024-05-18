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
 <p>問題：為什麼要帶出/入 uuid跟session_id?</p>
	
	Ａ裝置/Ｂ裝置
	    Session::getId();
	
	登入後 更新購物車資料所以我應該在寫一隻api
	而為什麼要在產出uuid?我已經有session_id了
	使用session紀錄
		1.可以依照使用的瀏覽器紀錄session_id 前提時效要夠長
		2.而uuid每次的生成都不一樣，所以uuid應該不適用在尚未登入的狀況下
		3.使用uuid應該也不是用在cart_id or cart_items_id 上 還是有什麼用途？


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
		    coupon_id
		    coupon_title
		    coupon_designated
		    coupon_deductible
		    coupon_discount
            },
            dicount:{
                discount_id
                discount_title
                discount_designated
                discount_deductible
                discount_discount
            }
        ],
        shippingFee
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
		    coupon_designated
		    coupon_deductible
		    coupon_discount
            },
            dicount:{
                discount_id
                discount_title
                discount_designated
                discount_deductible
                discount_discount
            }
        ],
        city,
        zone,
        [運送方式]
        note
        shippingFee
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
           shippingFee
	   coupon:{
		coupon_id
		coupon_title
		coupon_designated
		coupon_deductible
		coupon_discount
	    },
	    dicount:{
		discount_id
		discount_title
		discount_designated
		discount_deductible
		discount_discount
	    }
		
	}


<h1>[DELETE] /carts/item/{cart_item_id}</h1>

 	// 針對cart_item_id
  <p>回傳資料</p>
  
  	{
	   total
           shippingFee
	   coupon:{
		coupon_id
		coupon_title
		coupon_designated
		coupon_deductible
		coupon_discount
	    },
	    dicount:{
		discount_id
		discount_title
		discount_designated
		discount_deductible
		discount_discount
	    }
		
	}
	

<h1>[DELETE] /carts/{cart_id}</h1>

 	//針對store
<p>回傳資料</p>
  
  	{
	   total
           shippingFee
	   coupon:{
		coupon_id
		coupon_title
		coupon_designated
		coupon_deductible
		coupon_discount
	    },
	    dicount:{
		discount_id
		discount_title
		discount_designated
		discount_deductible
		discount_discount
	    }
		
	}
