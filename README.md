**Project Title:** Spammer Detection and Fake User Identification on Social Networks

**Description:**
This project implements a system for detecting spammers and identifying fake users on social networks. It leverages Django for the web framework, with separate applications for "Remote_User" (client-side functionalities) and "Tweet_Server" (admin/server-side functionalities). The system includes features for user registration, tweeting, reviewing tweets, sentiment analysis of tweets and reviews, and identification of spam and fake accounts based on user activities.

**Features:**

*   **User Authentication:**
    *   User registration and login.
    *   Tweet server login for administrative access.
*   **Tweet Management:**
    *   Users can post tweets.
    *   Tweets are analyzed for sentiment (Positive, Negative, Sexual, Offensive, Hateful, Volgar).
    *   Automatic flagging of user accounts as "Spam Account" if offensive or sexual words are used in tweets.
    *   Users can like and dislike tweets.
    *   View all tweets.
    *   View trending topics based on tweet content.
*   **Review System:**
    *   Users can review tweets.
    *   Reviews are analyzed for sentiment, similar to tweets.
    *   Automatic flagging of user accounts as "Fake User" if offensive, sexual, or vulgar words are used in reviews.
    *   View all user reviews.
*   **Admin/Server Features:**
    *   View all registered remote users.
    *   View all tweets and their analysis (ratings, dislikes, sentiment, location).
    *   View spam analysis on tweets, filterable by spam type.
    *   View spam analysis on reviews, filterable by spam type.
    *   View all spam users and their reasons for being flagged.
    *   View all fake users and their reasons for being flagged.
    *   Graphical representation of likes and dislikes using charts (line, pie, bar).
    *   View trending news/topics.

**Technologies Used:**

*   **Backend:**
    *   Python 3.6
    *   Django 2.0.5
*   **Database:**
    *   MySQL
*   **Frontend:**
    *   HTML
    *   CSS
    *   JavaScript (for charts using CanvasJS)
    *   Bootstrap 4.0.0
*   **Other:**
    *   Apache (implied by `wsgi.py` and general web server setup)

**Project Structure:**

```
Spammer_Detection/
├── spmmer_detection/
│   ├── Remote_User/
│   │   ├── migrations/
│   │   │   ├── 0001_initial.py
│   │   │   ├── 0002_usertweets_model.py
│   │   │   ├── 0003_usertweets_model_usefulcounts.py
│   │   │   ├── 0004_auto_20190429_1027.py
│   │   │   ├── 0005_usertweets_model_dislikes.py
│   │   │   ├── 0006_review_model.py
│   │   │   └── 0007_usertweets_model_names.py
│   │   ├── admin.py
│   │   ├── apps.py
│   │   ├── forms.py
│   │   ├── models.py
│   │   ├── tests.py
│   │   └── views.py
│   ├── Tweet_Server/
│   │   ├── admin.py
│   │   ├── apps.py
│   │   ├── models.py
│   │   ├── tests.py
│   │   └── views.py
│   ├── spmmer_detection/
│   │   ├── asgi.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   ├── Template/
│   │   ├── htmls/
│   │   │   ├── RUser/
│   │   │   │   ├── design.html
│   │   │   │   ├── dislikes.html
│   │   │   │   ├── login.html
│   │   │   │   ├── Post_Tweet.html
│   │   │   │   ├── ratings.html
│   │   │   │   ├── Register.html
│   │   │   │   ├── Review.html
│   │   │   │   ├── ViewAllTweets.html
│   │   │   │   ├── Viewreviews.html
│   │   │   │   ├── ViewTrending.html
│   │   │   │   └── ViewYourProfile.html
│   │   │   └── TServer/
│   │   │       ├── charts.html
│   │   │       ├── design1.html
│   │   │       ├── dislikeschart.html
│   │   │       ├── tweetserverlogin.html
│   │   │       ├── ViewTrendings.html
│   │   │       ├── Viewalltweets.html
│   │   │       ├── View_Fake_Users.html
│   │   │       ├── View_Remote_Users.html
│   │   │       ├── View_Spam_Analysis.html
│   │   │       ├── View_Spam_Reviews.html
│   │   │       ├── View_Spam_Users.html
│   │   │       └── View_User_Reviews.html
│   │   ├── images/
│   │   │   ├── bg1.jpg
│   │   │   ├── bg1.jpeg
│   │   │   ├── Icon.jpeg
│   │   │   └── login.jpg
│   │   └── media/
│   │       ├── button1.swf
│   │       └── text1.swf
│   └── manage.py
├── .idea/
│   ├── Spammer_Detection.iml
│   ├── misc.xml
│   ├── modules.xml
│   └── workspace.xml
└── spammerdetection.sql
```

**Setup and Installation:**

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd Spammer_Detection
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install dependencies:**
    ```bash
    pip install Django mysqlclient
    ```
    *(Note: `mysqlclient` requires MySQL development headers. On Ubuntu/Debian, install `libmysqlclient-dev`. On Windows, you might need a pre-compiled wheel or a different approach for MySQL connectivity.)*

4.  **Database Setup:**
    *   Create a MySQL database named `spammerdetection`.
    *   Import the provided SQL dump: `spammerdetection.sql` into your MySQL database.
    *   Ensure your MySQL server is running.
    *   Verify database configuration in `spmmer_detection/spmmer_detection/settings.py`:
        ```python
        DATABASES = {
            'default': {
                'ENGINE': 'django.db.backends.mysql',
                'NAME': 'spammerdetection',
                'USER':'root',  # Your MySQL username
                'PASSWORD': '',  # Your MySQL password
                'HOST' :'127.0.0.1',
                'PORT' :'3306',
            }
        }
        ```

5.  **Run Migrations:**
    ```bash
    python spmmer_detection/manage.py makemigrations Remote_User
    python spmmer_detection/manage.py migrate
    ```

6.  **Run the Development Server:**
    ```bash
    python spmmer_detection/manage.py runserver
    ```

7.  **Access the Application:**
    Open your web browser and navigate to `http://127.0.0.1:8000/`

**Usage:**

*   **User Login/Registration:** Access the main page (`/`) to log in or register as a new user.
*   **Tweet Server Login:** Access `/tweetserverlogin/` for administrative login.
    *   **Username:** `Server`
    *   **Password:** `Server`
*   Explore the different functionalities available for both regular users and the tweet server administrator.

**Sentiment Analysis Logic (Simplified):**

The `Remote_User/views.py` file contains the logic for sentiment analysis. It categorizes text (tweets and reviews) into:

*   **Positive:** Contains words like 'good', 'nice', 'better', 'best', 'excellent', 'extraordinary', 'happy', 'won', 'love', 'greate'.
*   **Negative:** Contains words like 'worst', 'waste', 'poor', 'error', 'imporve', 'bad'.
*   **Sexual:** Contains words like 'fuck', 'booms', 'suck', 'hottie', 'babe', 'beefy', 'hot'. (Flags user as "Spam Account" or "Fake User")
*   **Offensive:** Contains words like 'shut up', 'blast', 'kill', 'shoot', 'kick', 'kick out', 'murder'. (Flags user as "Spam Account" or "Fake User")
*   **Hateful:** Contains words like 'ridicules', 'nasty', 'horrible', 'bore', 'unhappy'.
*   **Volgar:** Contains words like 'stupid', 'bastard', 'brutal', 'blady'. (Flags user as "Spam Account" or "Fake User")

**Important Notes:**

*   The sentiment analysis is rule-based and very basic. For a production-level application, a more sophisticated NLP model would be required.
*   The flagging of "Spam Account" and "Fake User" is directly tied to the presence of specific keywords.
*   The project uses hardcoded admin credentials (`Server`/`Server`). In a real application, this should be managed securely.
*   Binary files (`.pyc`, `.iml`, `.sql`, image files, `.swf`) are included in the context, but typically only source code and necessary assets are version-controlled.

**Contact:**

For any questions or issues, please refer to the project's source code or contact the original developer.
