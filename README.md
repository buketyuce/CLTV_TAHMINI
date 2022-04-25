# CLTV_TAHMINI

FLO satış ve pazarlama faaliyetleri için roadmap belirlemek istemektedir. 

Şirketin orta uzun vadeli plan yapabilmesi için var olan müşterilerin gelecekte şirketesağlayacakları potansiyel değerin tahmin edilmesigerekmektedir.

# Veri seti Flo’dan son alışverişlerini 2020 - 2021 yıllarında OmniChannel olarak yapan müşterileringeçmiş alışveriş davranışlarından elde edilen bilgilerden oluşmaktadır

#master_id = Eşsiz müşteri numarası

#order_channel = Alışveriş yapılan platforma ait hangi kanalın kullanıldığı (Android, ios, Desktop, Mobile)

#last_order_channel = En son alışverişin yapıldığı kanal

#first_order_date = Müşterinin yaptığı ilk alışveriş tarihi

#last_order_date = Müşterinin yaptığı son alışveriş tarihi

#last_order_date_online = Müşterinin online platformda yaptığı son alışveriş tarihi

#last_order_date_offline = Müşterinin offline platformda yaptığı son alışveriş tarihi

#order_num_total_ever_online = Müşterinin online platformda yaptığı toplam alışveriş sayısı

#order_num_total_ever_offline = Müşterinin offline'da yaptığı toplam alışveriş sayısı

#customer_value_total_ever_offline = Müşterinin offline alışverişlerinde ödediği toplam ücret

#customer_value_total_ever_online = Müşterinin online alışverişlerinde ödediği toplam ücret

#interested_in_categories_12 = Müşterinin son 12 ayda alışveriş yaptığı kategorilerin liste

![1](https://user-images.githubusercontent.com/101973346/165012686-5849f26f-c349-4a58-bca5-6765c09b3de2.png)

# Aykırı değerleri baskılamak için gerekli olan outlier_thresholds ve replace_with_thresholds fonksiyonlarını tanımladım.
![2](https://user-images.githubusercontent.com/101973346/165012762-ac4fb980-822d-49dd-a110-8b7998032304.png)

#"order_num_total_ever_online","order_num_total_ever_offline","customer_value_total_ever_offline","customer_value_total_ever_online" değişkenlerinin aykırı değerleri varsa baskıladım.
![B](https://user-images.githubusercontent.com/101973346/165012836-36aefd0d-9ee0-4b0e-849c-00d32315ce29.png)

#Her müşterinin toplam alışveriş sayısı ve harcaması için yeni değişkenler oluşturdum.
![V](https://user-images.githubusercontent.com/101973346/165012935-d14d2ece-b26b-4396-a44c-850b19a0ee78.png)

#Tarih ifade eden değişkenlerin tipini date'e çevirdim.
![B](https://user-images.githubusercontent.com/101973346/165013029-e51c821d-a86e-49f5-99d2-fa41d1ad7a5a.png)

# CLTV VERİ YAPISININ OLUŞTURULMASI

#Veri setindeki en son alışverişin yapıldığı tarihten 2 gün sonrasını analiz tarihi olarak aldım.
![VF](https://user-images.githubusercontent.com/101973346/165013111-9e9c7814-43ee-4b68-9066-481c3b02bb02.png)

#customer_id, recency_cltv_weekly, T_weekly, frequency ve monetary_cltv_avg değerlerinin yer aldığı yeni bir cltv dataframe'i oluşturdum.
![ttt](https://user-images.githubusercontent.com/101973346/165013263-c7289212-65dc-40c0-b26a-8ec84d48d45b.png)

#BG/NBD modelini kurdum
![r](https://user-images.githubusercontent.com/101973346/165013349-7e76335c-a65b-44d9-a3f5-f043fb58f0f3.png)

#3 ay içerisinde müşterilerden beklenen satın almaları tahmin ettim ve exp_sales_3_month olarak cltv dataframe'ine ekledim
![bb](https://user-images.githubusercontent.com/101973346/165013439-d8cde5d8-c68b-4480-89ce-f0cc93a4f133.png)

#6 ay içerisinde müşterilerden beklenen satın almaları tahmin ettim ve exp_sales_6_month olarak cltv dataframe'ine ekledim
![hh](https://user-images.githubusercontent.com/101973346/165013512-3cb81f45-8568-4db9-ac54-210bf57e4cd2.png)

#3. ve 6.aydaki en çok satın alım gerçekleştirecek 10 kişiyi inceledim.
![b](https://user-images.githubusercontent.com/101973346/165013646-2c525769-56ec-42e3-98d3-71ec850d5084.png)
![o](https://user-images.githubusercontent.com/101973346/165013651-c002940e-3936-4a9b-b1f5-c13e505a9af9.png)

# Gamma-Gamma modelini fit ettim. Müşterilerin ortalama bırakacakları değeri tahminleyip exp_average_value olarak cltv dataframe'ine ekledim
![tt](https://user-images.githubusercontent.com/101973346/165013750-4828c65b-f08f-4997-9595-0dfc54e6d892.png)

#3. 6 aylık CLTV hesapladım ve cltv ismiyle dataframe'e ekledim
![ttt](https://user-images.githubusercontent.com/101973346/165013822-3b5ff151-e48d-49ac-b423-d474318781ca.png)

#CLTV değeri en yüksek 20 kişiyi gözlemledim.
![vvbv](https://user-images.githubusercontent.com/101973346/165013923-9b8c7291-b208-4d3d-a77f-d6a81c171e37.png)

# CLTV'ye Göre Segmentlerin Oluşturulması
#1. 6 aylık standartlaştırılmış CLTV'ye göre tüm müşterileri 4 gruba (segmente) ayırdım ve grup isimlerini veri setine ekledim.
![f](https://user-images.githubusercontent.com/101973346/165014042-c967ae66-781e-4724-af0c-7cb3885e6ca8.png)
![hghghg](https://user-images.githubusercontent.com/101973346/165014081-44762213-cd3c-4328-83b4-40c8b0836b23.png)

# Tüm süreci fonksiyonlaştırdım.




