[requirements.txt](https://github.com/user-attachments/files/22147618/requirements.txt)
telethon==1.28.5
[forwarder.py](https://github.com/user-attachments/files/22147634/forwarder.py)
{\rtf1\ansi\ansicpg1251\cocoartf2639
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;\f1\fnil\fcharset0 AppleColorEmoji;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 from telethon import TelegramClient, events\
import asyncio\
import os\
\
api_id = int(os.getenv('API_ID'))\
api_hash = os.getenv('API_HASH')\
source_channel = int(os.getenv('SOURCE_CHANNEL'))\
target_channel = int(os.getenv('TARGET_CHANNEL'))\
\
client = TelegramClient('session', api_id, api_hash)\
\
@client.on(events.NewMessage(chats=source_channel))\
async def handler(event):\
    await client.forward_messages(target_channel, event.message)\
    print(f"
\f1 \uc0\u9989 
\f0  \uc0\u1055 \u1077 \u1088 \u1077 \u1089 \u1083 \u1072 \u1085  \u1087 \u1086 \u1089 \u1090 : \{event.message.id\}")\
\
async def main():\
    print("
\f1 \uc0\u55357 \u56960 
\f0  \uc0\u1041 \u1086 \u1090  \u1079 \u1072 \u1087 \u1091 \u1097 \u1077 \u1085 ... \u1046 \u1076 \u1091  \u1085 \u1086 \u1074 \u1099 \u1093  \u1087 \u1086 \u1089 \u1090 \u1086 \u1074 ")\
    await client.start()\
    await client.run_until_disconnected()\
\
asyncio.run(main())\
}
