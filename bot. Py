import logging
from telegram import Update, InlineKeyboardButton, InlineKeyboardMarkup
from telegram.ext import ApplicationBuilder, CommandHandler, CallbackQueryHandler, ContextTypes

# Logging setup
logging.basicConfig(format='%(asctime)s - %(name)s - %(levelname)s - %(message)s', level=logging.INFO)

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    keyboard = [
        [InlineKeyboardButton("🪑 Maa Ambey Furniture", callback_query_data='furniture')],
        [InlineKeyboardButton("💎 Raj Laxmi Jewellers", callback_query_data='jewellers')],
        [InlineKeyboardButton("📞 Contact Us", callback_query_data='contact')]
    ]
    reply_markup = InlineKeyboardMarkup(keyboard)
    
    await update.message.reply_text(
        "Namaste! 🙏\n\nMain aapka digital business assistant hoon. Aap kis shop ki jankari lena chahte hain?",
        reply_markup=reply_markup
    )

async def handle_buttons(update: Update, context: ContextTypes.DEFAULT_TYPE):
    query = update.callback_query
    await query.answer()

    if query.data == 'furniture':
        text = "🪑 *Maa Ambey Furniture*\n\nHumare yahan Sofa, Bed, aur Dining Table ki sabse badhiya range milti hai.\n\n📍 Location: Ajmer"
    elif query.data == 'jewellers':
        text = "💎 *Raj Laxmi Jewellers*\n\nSone aur chaandi ke vishwasniya gehne. Hum latest designs aur shuddhata ka pura dhyan rakhte hain.\n\n📍 Location: Ajmer"
    elif query.data == 'contact':
        text = "📞 *Contact Details*\n\nShop par visit karne ke liye Ajmer location par aayein."

    await query.message.reply_text(text=text, parse_mode='Markdown')

if __name__ == '__main__':
    # YAHAN APNA REAL TOKEN PASTE KAREIN
    TOKEN = "8332326138:AAHg_FPdWis4xSqTjj2js9PNZPWGpixNUEY"

    
    app = ApplicationBuilder().token(TOKEN).build()
    app.add_handler(CommandHandler("start", start))
    app.add_handler(CallbackQueryHandler(handle_buttons))
    
    print("Bot chalu ho gaya hai...")
    app.run_polling()
