import xml.etree.ElementTree as ET

books ={}
buy = {} #list of buy orders corresponding to bookid
sell = {}

addBooks(bookid):
    if bookid not in books:
            books.add[bookid]
    

DeleteOrder(bookid, operation, ord):
    if(operation == "BUY"):
        lis = buy[bookid]
        for i in range (0, len(lis)):
            if(lis[i] == ord):
                del lis[i]
                break

addOrder(bookid, operation, price, volume, orderId):
    ls_buy = buy[bookid]
    ls_sell = sell[bookid]
    if(operation == "SELL" and bookid in books and len(ls_buy != 0)):
        
        for i in range ( len(ls_buy) -1, 0):

            ord= ls_buy[i]
            ind= ord.find('@')
            vol_buy = ord(0, ind)
            pri_buy = ord(ind+1, len(ord))


            if(price <= pri_buy):

                if(volume >= vol_buy):
                    volume = volume - vol_buy
                    DeleteOrder(bookid, "BUY", ord)
                
                elif(volume < vol_buy):
                    vol_buy = vol_buy - volume
                    volume =0
                    ord = vol_buy + "@" + pri_buy
                    ls_buy[i] = ord

            if(volume ==0):
                break
        if(volume != 0):
            if book in books:
                sell[bookid].add((volume + "@" + price))
                sell[bookid].sort()
            else:
                ls = []
                books.add(bookid)
                ls.add((volume + "@" + price))
                book[bookid] = ls

    if(operation == "BUY" and (bookid in books) and len(ls_sell != 0)):
        
        for i in range ( len(ls_sell) -1, 0):

            ord= ls_sell[i]
            ind= ord.find('@')
            vol_sell = ord(0, ind)
            pri_sell = ord(ind+1, len(ord))


            if(price <= pri_sell):

                if(volume >= vol_sell):
                    volume = volume - vol_sell
                    DeleteOrder(bookid, "SELL", ord)
                
                elif(volume < vol_sell):
                    vol_sell = vol_sell - volume
                    volume =0
                    ord = vol_sell + "@" + pri_sell
                    ls_sell[i] = ord

            if(volume ==0):
                break
        if(volume != 0):
            if book in books:
                buy[bookid].add((volume + "@" + price))
                buy[bookid].sort()
            else:
                ls = []
                books.add(bookid)
                ls.add((volume + "@" + price))
                book[bookid] = ls


tree = ET.parse("orders.xml")
root = tree.getroot()

print(root) #orders
