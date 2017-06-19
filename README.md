YouTubePlaylist
===============

A sample Android application which demonstrates the use of the [YouTube Data API v3](https://developers.google.com/youtube/v3/).

This sample app makes use of the [YouTube Data API v3 classes](https://developers.google.com/resources/api-libraries/documentation/youtube/v3/java/latest/) to fetch a YouTube [Playlist](https://developers.google.com/resources/api-libraries/documentation/youtube/v3/java/latest/com/google/api/services/youtube/model/Playlist.html) using [RxJava](https://github.com/ReactiveX/RxJava) to perform the network I/O operation on a background thread where the list of [Video](https://developers.google.com/resources/api-libraries/documentation/youtube/v3/java/latest/com/google/api/services/youtube/model/Video.html)'s contained in the playlist are extracted and then handed off to the UI thread for rendering.  The list of video's are rendered using a [RecyclerView](https://developer.android.com/reference/android/support/v7/widget/RecyclerView.html) of [CardView](https://developer.android.com/reference/android/support/v7/widget/CardView.html)'s in the [YouTubeRecyclerViewFragment](app/src/main/java/com/akoscz/youtube/YouTubeRecyclerViewFragment.java).

The [Android data binding support tools](http://developer.android.com/tools/data-binding/guide.html) are then used to bind the the data to the UI. The [PlaylistCardAdapter](app/src/main/java/com/akoscz/youtube/PlaylistCardAdapter.java) is responsible for binding a [VideoViewModel](app/src/main/java/com/akoscz/youtube/viewmodel/VideoViewModel.java) instance to the [Video Card](app/src/main/res/layout/youtube_video_card.xml) layout.


[Picasso](https://github.com/square/picasso) is used for [downloading](app/src/main/java/com/akoscz/youtube/databinding/BindingUtils.java) and caching the video thumbnail images.
And lastly a [retained fragment](http://developer.android.com/guide/topics/resources/runtime-changes.html#RetainingAnObject) is used to persist the [Playlist](app/src/main/java/com/akoscz/youtube/model/Playlist.java) datamodel across orientation changes.

## Setup
  
  * Register your application with the [Google Developer Console](https://developers.google.com/youtube/registering_an_application).
  * Create an ["Api Key"](https://developers.google.com/youtube/registering_an_application#Create_API_Keys)
  * Edit [ApiKey.java](app/src/main/java/com/akoscz/youtube/ApiKey.java) and update `YOUTUBE_API_KEY` with your applications "Api Key"
  * Edit [YouTubeActivity.java](app/src/main/java/com/akoscz/youtube/YouTubeActivity.java) and update `YOUTUBE_PLAYLIST` to point to your YouTube [playlist](https://www.youtube.com/playlist?list=PLWz5rJ2EKKc_XOgcRukSoKKjewFJZrKV0).

*NOTE:* You MUST have a valid API key for this sample application to work. Remember, when you register your application with the Google Developer Console you need to enable the YouTube Data API.
  
## Application Dependencies
  * [`com.android.support:cardview-v7:25.2.0`](https://developer.android.com/tools/support-library/features.html#v7-cardview)
  * [`com.android.support:recyclerview-v7:25.2.0`](https://developer.android.com/tools/support-library/features.html#v7-recyclerview)
  * [`com.android.support:appcompat-v7:25.2.0`](https://developer.android.com/tools/support-library/features.html#v7-appcompat)
  * [`com.squareup.picasso:picasso:2.5.2`](https://github.com/square/picasso)
  * [`com.google.apis:google-api-services-youtube:v3-rev182-1.22.0`](https://developers.google.com/api-client-library/java/apis/youtube/v3)
  * [`com.google.http-client:google-http-client-android:1.20.0`](https://github.com/google/google-http-java-client)
  * [`com.google.api-client:google-api-client-android:1.20.0`](https://github.com/google/google-api-java-client)
  * [`com.google.api-client:google-api-client-gson:1.20.0`](https://github.com/google/google-api-java-client)
  * [`com.google.dagger:dagger:2.10-rc2`](https://github.com/google/dagger)
  * [`io.reactivex:rxandroid:1.0.1`](https://github.com/ReactiveX/RxAndroid)
  * [`io.reactivex:rxjava:1.0.14`](https://github.com/ReactiveX/RxJava)
  
## Build Script Dependencies
  * [`com.android.tools.build:gradle:2.3.0`](https://developer.android.com/tools/revisions/gradle-plugin.html)
  * [`me.tatarka:gradle-retrolambda:3.6.0`](https://github.com/evant/gradle-retrolambda)

## Screenshots
__Phone__: Single Column Portrait and Landscape

![](screenshots/phone-port.png)

__Tablet__: 7" and 9" (sw600) 2 Columns Portrait, 3 Columns Landscape

![](screenshots/tablet_7_9-port.png)
![](screenshots/tablet_7_9-land.png)

__Tablet__: 10" (sw800) 3 Columns Portrait and Landscape

![](screenshots/tablet_10-port.png)
![](screenshots/tablet_10-land.png)

## License

  * [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)
  
