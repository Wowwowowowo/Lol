import telebot
bot = telebot.TeleBot('6065230777:AAGca3wKj1Q3YypvbZGaX-3KsAuhNGT2gbs')
oput = 0
dengi = 5000
name = 'Игрок'
bisnes = False
pribil_bisnes = 0
@bot.message_handler(commands=['start'])
def start(message):
    bot.send_message(message.chat.id,'Привет🤟, я TGB бот твой майнинг бот ты  можешь делать бизнес получать деньги и быть милионером😁\nчтобы вывести свой баланс напиши /b\nвсе команды в функции /help')

@bot.message_handler(commands=['b'],content_types=['text'])
def balans(message):
		global dengi
		bot.send_message(message.chat.id,f'🎮Ваш никнейм = {name}\n🤑Деньги = {dengi}\n🚖Ваш опыт = {oput}')

@bot.message_handler(commands=['help'])
def help(message):
			bot.send_message(message.chat.id,'Вывести баланс - /b\nбизнес - /build_bisnes, /bisnes, /rabotat, /sobr 💽')

@bot.message_handler(commands=['build_bisnes'])
def bisnes(message):
	global dengi
	bot.send_message(message.chat.id,'Поздровляю ты построил бизнес 😚\nбизнес стоил 500 руб\nпосмотри свои данные бизнеса командой /bisnes')   
	dengi -= 500
@bot.message_handler(commands=['bisnes'])
def work(message):
    global pribil_bisnes
    pribil = pribil_bisnes       
    pribil_bisnes += 100
    bot.send_message(message.chat.id,f'Ваш бизнес\n🤑Прибыль = {pribil}')
@bot.message_handler(commands=['rabotat'])
def rabota(message):
      global pribil_bisnes
      bot.send_message(message.chat.id,'ты получил 100 руб на баланс бизнеса 😇')
      pribil_bisnes += 100
@bot.message_handler(commands=['sobr'])
def sobr(message):
    global dengi
    global pribil_bisnes
    bot.send_message(message.chat.id,f'молодец ты собрал - {pribil_bisnes} руб я поздровляю 😘')
    dengi += pribil_bisnes
    pribil_bisnes = 0
    
    
	
bot.infinity_polling()
