下單流程

    1.使用者下單如果有登入紀錄member_id
        如果未登入紀錄member_uuid
        下單後產生 交易uuid 產生一筆綠界資料
        綠界交易成功後會自己回丟

    2.如果取消訂單？
        排成判斷
    3.付款方式有幾種？
        打綠界 api
    4.寄貨方式有幾種？
        信用卡 信用卡分期 超商 虛擬 atm
    5.退貨流程？
        研究

綠界資料表（ecPay）

    MerchantID String(10) 
    MerchantTradeNo String(20)
    StoreID String(20)
    RtnCode Int
    RtnMsg String(200)
    TradeNo String(20)
    TradeAmt Int
    PaymentDate String(20)
    PaymentType String(20)
    PaymentTypeChargeFee Number 
    TradeDate String(20)
    SimulatePaid　Int
    CustomField1 String(50)
    CustomField2 String(50)
    CustomField3 String(50)
    CustomField4 String(50)
    CheckMacValue String
    transaction_id
    store_id
    provider ( 綠界, paypal, 藍星 )
    provider_raw_data  ( 綠界, paypal )
    product_name
    product_id
    product_specification_id
    product_specification_name
    

有疑問（是否少一張資料表）

    Transaction 
        =================?
        pay_method
        transaction_no
        discount
        status  ( 代付款，退貨，取消 )
        provider ( 綠界, paypal, 藍星 )
        provider_raw_data  ( 綠界, paypal )

    Transaction_item
        status  ( 代付款，退貨，取消 )
        provider_return_raw_data  ( 綠界, paypal )
        store_id
        coupon_id
        coupon_type ( 全館，單品 )
        coupon_name
        transaction_id
        product_name
        product_id
        product_specification_id
        product_specification_name
        寄件地址
        統編
        三聯
        載具
        發票
        coupon





