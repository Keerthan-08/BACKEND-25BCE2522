# BACKEND-25BCE2522
GDG 2025/26 BACKEND Round 2 (Incomplete)
I’d like to walk you through the project. I dedicated the majority of my time to the AIML component, which was my primary focus and area of interest. I believe that part is solid.

Regarding the backend, I have to be honest—I wasn't able to complete it to the level I wanted.
Since I was learning Django and MongoDB from scratch without support, the time constraints were just too tight. 
I have some generated code and a basic structure, but the backend task remains unfinished. 
I prioritized ensuring the AI model itself was working correctly rather than submitting a broken backend integration.
I attempted to build the integration using Django and MongoDB, but since I was learning these tools on the fly, I couldn't complete the full implementation in time.
I used GenAI to help understand the flow and generate some boilerplate, but debugging the integration took longer than expected.
So, while the AI logic is ready, the backend connection is currently incomplete

But i will make sure i will work on that as well in future days 

So, here is the full structure of the project I attempted to build.
I organized it into three main areas: the environment, the project configuration, and the actual chat app."

1. The Root Folder (realtimec):
This is the main container for everything.

  venv (Virtual Environment): 
  I set this up first. It’s supposed to be a clean, isolated space for all my software libraries. 
  I installed Django, Channels, and the Djongo connector here.

  manage.py: 
  This is the standard control script for Django.
  I used it to try and run the server, but because of the database errors I mentioned earlier, running commands like migrate usually crashes the system.

2. The Configuration Folder (myproject)
This folder holds the settings for the whole website.

  settings.py: 
  This is where I tried to connect Django to MongoDB.
  I added the configurations that AI gave me.
  The 'Djongo' library conflicts with my Python version, causing the whole connection to break.

  asgi.py: 
  Standard Django uses wsgi.py, but for real-time chat, you need this file instead.
  The AI generated this to act as a gateway for live, asynchronous connections. It works in theory, but it can't function without a working database.

  urls.py (Main): 
  This is the main entry point. It just directs flow to the specific Chat app.

3. The App Folder (chat)
This is where all the logic resides. I had the AI generate most of these files to handle the messaging features.

  apps.py: 
  This is a simple file that just registers the app with Django. It tells the project, 'The chat app is installed.'

  models.py: 
  I defined the data structure here. I told it I wanted a 'Message' model with a sender, receiver, and timestamp. 
  The code is correct(I verified using AI), but because the database connection is broken, I can't actually save any messages.

  serializers.py: 
  I needed to convert database data into JSON for the frontend.
  This script handles that translation, but since there is no data coming from the database, this file is basically useless right now.

  views.py:
  This handles the API requests, like fetching chat history.
  It tries to talk to MongoDB to get old messages, but because the driver is incompatible, it just returns errors.

  urls.py (Chat): 
  This handles the routing for standard web requests. It maps URLs to the views I just mentioned.

  The Real-Time Files:
  These last two are specific to the live chat feature:

  routing.py:
  Think of this as the URL router for WebSockets.
  The AI set this up to say, 'If a user connects to ws/chat, send them to the Consumer.' The path works, but the destination fails.

  consumers.py: 
  It contains the logic for the live socket connection.
  It accepts the user's connection, but the moment it tries to save a message to the broken MongoDB database, the connection snaps and the chat fails.
