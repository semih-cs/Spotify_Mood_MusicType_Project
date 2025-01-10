# DSA210 Project: Analyzing the Correlation Between My Music Preferences and Emotional States

I embarked on this project to investigate whether there is a meaningful relationship between my Spotify listening habits and my emotional state over a one-year period (November 2023 – November 2024). I wanted to see if music features—such as genre, popularity, and various Spotify audio attributes—could reflect or influence how I feel as time progresses.

## 1. Introduction and Project Goal

My main goal was to analyze my personal Spotify data to see if any patterns emerged regarding my music preferences and my potential emotional shifts. Specifically, I focused on:

* Identifying which songs and artists I listened to the most over time
* Checking whether there was a noticeable change in the moods of the tracks I listened to each month
* Determining if there was any statistical correlation—positive or negative—between the passage of months and the "dominant mood" of my most-played songs

## 2. Data Sources and Workflow

### Spotify Streaming History (JSON)
* I obtained a JSON file with details like track names, artist information, timestamps (endTime), and msPlayed (play duration)
* I converted the endTime column to a datetime format and created a minutes_played column to measure total listening duration per track in minutes

### Spotify API
* Using a Python script, I authenticated with Spotify's API
* For each monthly top track, I fetched metadata (e.g., popularity, genres) to categorize my music by a "dominant_mood"

### Code Organization
* `daily-listening.ipynb` and `the_days_of_the_month_I_listened_music_most.ipynb` helped me visualize daily trends and the days I listened to music the most
* `most_listened_artist.ipynb` and `most_listened_artist_by_month.ipynb` helped me track which artists dominated my listening time overall and on a monthly basis
* `most_listened_songs_by_month.ipynb` zeroed in on my top track each month
* `type.ipynb` did the heavier lifting: it combined monthly top tracks with the Spotify API's metadata to produce a `music_mood_analysis.csv` file containing the "dominant_mood" for each monthly top track
* Finally, `correlation.ipynb` took that CSV file, plotted these tracks on a month-by-month basis, and calculated a correlation coefficient for my mood trends over time

## 3. Key Code Components and Logic

### Data Loading and Grouping
I repeatedly used functions that load my JSON file, convert timestamps, and group by month, day, or artist to figure out which songs or artists I listened to most.

### Mood Analysis
In my main script (`type.ipynb`), I defined a function that assigns each track a "dominant_mood" by checking its genre and popularity. For instance, certain genres increase the "happy" or "energetic" score, while low popularity might steer the mood toward "melancholic."

### Correlation and Trend Line
In `correlation.ipynb`, I took the final `music_mood_analysis.csv` and isolated the months between November 2023 and November 2024. Each month was assigned a numeric value (1, 2, 3, etc.), and I plotted my "mood_value" over time. I used a linear regression to see if there was an upward or downward trend in my music's mood as the months passed.

## 4. Results

### Listening Habits
Through my daily and monthly analyses, I discovered which days I listened to music the most, as well as which artists I tended to favor. Certain periods showed spikes, possibly reflecting my schedule or personal events.

### Top Artists and Songs
My notebooks revealed a few standout artists I listened to repeatedly throughout the year. I also identified a monthly top song, offering a clear perspective on how my taste evolved (or stayed the same) from month to month.

### Mood Analysis
When I combined the Spotify API's metadata with my streaming data, I could see an overview of how each month's most-listened track aligned with different moods. These moods ranged from "happy" or "energetic" to "calm," "intense," or "melancholic."

### Correlation Findings
My final chart plotted these moods over each month in the chosen time frame. I calculated the correlation coefficient to measure how strongly the "mood_value" changed from November 2023 to November 2024. A positive coefficient suggested that my listening habits leaned toward higher-energy or happier tracks over time, whereas a negative coefficient would have implied a shift toward calmer or more melancholic music. A low absolute value would indicate no strong pattern.

## 5. Conclusion

By examining a full year of personal Spotify data, I gained a clearer picture of how my music choices relate to my emotional states. I found that plotting monthly top songs and calculating a correlation coefficient offered valuable insights into whether I gradually shifted toward certain moods or if my tastes stayed relatively consistent. This approach was a practical way to quantify something as subjective as personal mood and music preference. Overall, it was enlightening to see my listening trends laid out with data-driven clarity, and I hope to explore this connection further as more listening data becomes available.
