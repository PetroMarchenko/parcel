# parcel
Задача: отобразить информацию по накладной и отобразить ее движение на карте google.maps			
Ограничения: 			
	1. Проверка на заполнение полей ЭН и номер телефона		
	1. Проверка на наличие номера ЭН в базе		
	2. Проверка на соответствие введенного номера телефона накладной		
			
Реализация:			
			
	Модели		
	Barcode	1. Основная информация по накладной	
		2. Рилейшны:	
			штрихкод может много раз сканироваться hasMany Scan::class
			у штрихода есть город-отправитель со своими свойствами -> hasOne City::class
			у штрихода есть город-получатель со своими свойствами -> hasOne City::class
			
	Scan	1. Информация "когда и на каком подразделении сканировался barcode"	
		2. Рилейшны:	
			сканировка происходит на складе -> hasOne Warehouse::class
			сканировки принадлежат штрихкодам -> belongsTo Barcode::class
			
	Warehouse	1. Справочник складов Новой Почты. Название отделение + id города	
		2. Рилейшны:	
			склад принадлежит одному городу -> hasOne City::class
			
			
	Warehouse	1. Название и геокоординаты города	
			
			
			
Примечание:			
	Посылка сканируется несколько раз в прелелах города (отделение на загрузку, терминал на выгрузку, терминал на загрузку в другой город)		
	Чтобы не плодить маркеры на карте, оставляем только первую сканировку в пределах одного города.		



Дамп базы в файле Database dump


Данные для проверки работоспособности в файле Накладные.xls
