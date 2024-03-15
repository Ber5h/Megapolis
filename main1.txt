# Использован язык программирования Python

'''Описание встречаемых в программе переменных:
res_dict - словарь, хранящий в качестве ключа название компании,
 в качестве значения - количество устройств в данной компании
f - файл, с которым в данный момент идёт работа
a - строка считываемого файла
t - строка файла, с которой в данный момент идёт работа, в удобном для записи/чтения формате
'''

res_dict = {}

with open('devices.csv') as f:
    for a in f.readlines()[1:]:  # [1:] чтобы исключить строчку с заголовком
        t = list(a.split(sep=';'))
        if t[0] in res_dict.keys():
            res_dict[t[0]] += 1
        else:
            res_dict[t[0]] = 1
with open('count_company.csv', 'w') as f:
    t = 'Company;countProduct'
    f.write(t)
    for x in res_dict.keys():
        t = '\n' + x + ';' + str(res_dict[x])
        f.write(t)
with open('count_asus.txt', 'w', encoding='utf-16') as f:
    f.write('От компании Asus у нас есть ' + str(res_dict['Asus']) + ' товаров.')
