from telebot import TeleBot, types

bot = TeleBot("7582799308:AAEw6ZBeTx_OQhq0RscW-abuY_TopR5L8EY")

@bot.message_handler(commands=['start'])
def start(message):
    # User ka first name lena
    user_name = message.from_user.first_name
    
    # Custom inline buttons banayein
    markup = types.InlineKeyboardMarkup(row_width=2)
    btn1 = types.InlineKeyboardButton("☆ Add me to your group ☆", url="https://t.me/@Movielolni_bot?startgroup=true")
    btn2 = types.InlineKeyboardButton("💸 Earn Money 💸", callback_data="earn_money")
    btn3 = types.InlineKeyboardButton("• Updates •", callback_data="updates")
    btn4 = types.InlineKeyboardButton("• Commands •", callback_data="commands")
    btn5 = types.InlineKeyboardButton("• About •", callback_data="about")
    btn6 = types.InlineKeyboardButton("✨ Buy Subscription: Remove Ads ✨", callback_data="subscribe")
    markup.add(btn1, btn2, btn3, btn4, btn5, btn6)

    # Greeting message ke saath user ka naam
    greeting_message = f"Hey {user_name}, good evening 👋\nI am the most powerful auto filter bot with premium features."
    
    # Message bhejne ke liye bot.send_message ka use karein
    bot.send_message(message.chat.id, greeting_message, reply_markup=markup)

bot.polling()
