# Wear OS 3: Great Opportunity for Developers

</br>

For over a decade, Samsung and Google have worked together to push mobile technology forward across smartphones, tablets and foldables but Smartwatches are the next step in mobile computing and we’re truly excited about the future of wearables. Recently, Samsung unveiled its new ***Galaxy Watch 4*** with ***Wear OS*** Powered by Samsung. 

Samsung has had a long history in smartwatches, with a lot of experimentation in features and software ideas. The company's latest Galaxy Watch 4 represents a new phase. Its software is the result of a partnership with Google, the first entry in what could be a whole new line of Android watches using Wear OS 3. The new Galaxy Watch 4, has new health features (snore detection and a body analysis sensor estimating BMI and muscle-fat tone using electrical impedance). It also has a completely new OS compared to previous Samsung watches: one that's built off Google's software but also has Samsung's health and app features. It'll hook into core Android and Samsung apps. 

</br>

<p align="center">
  <img src="https://fdn.gsmarena.com/imgroot/news/21/08/samsung-galaxy-watch4-series-ofic/-1220x526/gsmarena_001.jpg" alt="Samsung Galaxy Watch 4" width="75%" />
</p>


</br>
That sounds pretty good but the question is should we start apps developing for Wear OS 3 or Samsung Galaxy Watch 4 ? Let's find the answer!


## What is Wear OS 3?

Wear OS 3.0 is the latest edition of the smartwatch OS – and one of the biggest updates ever to the platform.  It's being co-developed by Google and Samsung, the latter of which has adopted Wear OS in lieu of its long-time Tizen platform. It brings some notable changes compared to previous iterations of Wear OS, which should give it a boost when compared to both Google and Samsung's efforts in the space, combining the best of both companies. 

Wear OS 3.0 in brief:

- Wear OS to get biggest ever update
- Built on Android 11
- Unified OS with Wear OS and Tizen merging
- Samsung Galaxy Watch 4 and Classic are first Wear 3.0 smartwatches
- Some existing Wear smartwatches will get the upgrade in 2022
- Longer battery life (2 days) and new app switching feature
- New and improved apps for Wear OS


## New Features

While hardware manufacturers can tweak the sorts of functionality their Wear OS watches bring to the table, Wear OS itself comes with a fundamental feature set that can be expanded upon – depending on factors like price point or target audience. So let's talk about some new cool features of Wear OS 3, so that you can make a decision.

Basics include notification synchronization with a connected smartphone, clock, timer and alarm functionality, fitness tracking (with support for various activities, along with heart rate and route tracking – with GPS support), contactless payments (via NFC) using Google Pay, Google Assistant queries, making and taking calls on-wrist, audio playback, and third-party app and watch face support, by way of the Google Play Store.



### Compose for Wear OS

Compose for Wear OS is now available! Design your app with familiar UI components adapted for the watch. Compose for Wear OS is in developer preview, with new samples and documentation to help you get started. Most of the Wear related changes you make will be at the top architectural layers.

</br>
<p align="center">
  <img style="align:center" src="https://1.bp.blogspot.com/-prFJa-FMP5k/YWWqhhU75dI/AAAAAAAAQ_w/9kgz1krIxPMkMDovYoTNVFuBM9W1vMXLgCLcBGAsYHQ/s0/image10.png" alt="Samsung Galaxy Watch 4" width="25%" />
</p>
</br>

That means many of the dependencies you already use with Jetpack Compose don't change when targeting Wear OS. For example, the UI, Runtime, Compiler, and Animation dependencies will remain the same. However, you will need to use the proper Wear OS Material, Navigation, and Foundation libraries which are different from the libraries you have used before in your mobile app.

</br>

|<p>**Wear OS Dependency**</p><p>(androidx.wear.\*)</p>|**Comparison**|<p>**Mobile Dependency**</p><p>(androidx.\*)</p>|
| :-: | :-: | :-: |
|[androidx.wear.compose:compose-material](https://developer.android.com/reference/kotlin/androidx/wear/compose/material/package-summary)|***instead of***|androidx.compose.material:material **₁**|
|[androidx.wear.compose:compose-navigation](https://developer.android.com/reference/kotlin/androidx/wear/compose/navigation/package-summary)|***instead of***|androidx.navigation:navigation-compose|
|[androidx.wear.compose:compose-foundation](https://developer.android.com/reference/kotlin/androidx/wear/compose/foundation/package-summary)|***in addition to***|androidx.compose.foundation:foundation|

</br>

Here's an example build.gradle file:

</br>

```gradle
// Example project in app/build.gradle file
dependencies {
    // Standard Compose dependencies...

    // Wear specific Compose Dependencies
    // Developer Preview starts with Alpha 07, with new releases coming soon.
    def wear_version = "1.0.0-alpha07"
    implementation "androidx.wear.compose:compose-material:$wear_version"
    implementation "androidx.wear.compose:compose-foundation:$wear_version"

    // For navigation within your app...
    implementation "androidx.wear.compose:compose-navigation:$wear_version"

    // Other dependencies...
}

```
</br>

Let's explore some composables you can start using today.

As a general rule, many of the Wear composables that are equivalent to the mobile versions can use the same code. The code for styling color, typography, and shapes with MaterialTheme is identical to mobile as well.

For example, to create a Wear OS button your code looks like this:

</br>

```Java

Button(
    modifier = Modifier.size(ButtonDefaults.LargeButtonSize),
    onClick = { /*...*/ },
    enabled = enabledState
) {
    Icon(
        painter = painterResource(id = R.drawable.ic_airplane),
        contentDescription = "phone",
        modifier = Modifier
            .size(24.dp)
            .wrapContentSize(align = Alignment.Center),
    )
}

```

</br>



<img align="left" src="https://lh4.googleusercontent.com/w43qtaJV2QVPQrqbdCa1Hfnfg4rL_eGCD5wWKhCUJblfSzjUu38yVLP1zdLAHMrVO0X9XpF2H8e6h-pUi3zcMdO4YwEARwhheYhQoFA6eUmXpwCakofIciU1v0aVJsNtgRQmxm8SF_ADombUBRW9OKQQxNErqxE5wesM_VC7QLNYWr5J=s0" alt="Samsung Galaxy Watch 4 Icon" width="12%" />
The code above is very similar to the mobile side, but the library creates a Wear OS optimized version of the button, that is, a button circular in shape and sized by *ButtonDefaults* to follow Wear OS Material Guidelines. 



</br> </br> </br>

### Tiles
Also the new Wear OS 3 will make the API for its Tile Widget available for third-party developers to make custom Tiles that will work for all watches. Also, tiles like Adidas running, Golfpad, Flo and Outdooractive are part of the third party tiles in the works. Using the Tiles API requires targeting API level 26 or higher.

</br>

<p align="center">
  <img src="https://developer.android.com/images/wear/tile.gif" alt="Wear OS 3 Tiles" width="70%" />
</p>

</br>

To start providing Tiles from your app, include the following dependencies in your app's build.gradle file. 

</br>

```gradle

dependencies {
    // Use to implement support for wear tiles
    implementation "androidx.wear.tiles:tiles:1.1.0-alpha03"

    // Use to utilize components and layouts with Material design in your tiles
    implementation "androidx.wear.tiles:tiles-material:1.1.0-alpha03"

    // Use to preview wear tiles in your own app
    debugImplementation "androidx.wear.tiles:tiles-renderer:1.1.0-alpha03"

    // Use to fetch tiles from a tile provider in your tests
    testImplementation "androidx.wear.tiles:tiles-testing:1.1.0-alpha03"
}

```

</br>

To provide a Tile from your application, create a class that extends TileService and implement the methods, as shown in the following code sample:

</br>

```Java

public class MyTileService extends TileService {
    private static final String RESOURCES_VERSION = "1";

    @NonNull
    @Override
    protected ListenableFuture<Tile> onTileRequest(
        @NonNull TileRequest requestParams
    ) {
        return Futures.immediateFuture(new Tile.Builder()
            .setResourcesVersion(RESOURCES_VERSION)
            .setTimeline(new Timeline.Builder()
                .addTimelineEntry(new TimelineEntry.Builder()
                    .setLayout(new Layout.Builder()
                        .setRoot(new Text.Builder()
                            .setText("Hello world!").build()
                        ).build()
                    ).build()
                ).build()
            ).build()
        ).build();
   }

   @NonNull
   @Override
   protected ListenableFuture<Resources> onResourcesRequest(
       @NonNull ResourcesRequest requestParams
   ) {
       return Futures.immediateFuture(new Resources.Builder()
               .setVersion(RESOURCES_VERSION)
               .build()
       );
   }
}

```

</br>

Next, add a service inside the <application> tag of your AndroidManifest.xml.

</br>

```XML

<service
   android:name=".MyTileService"
   android:label="@string/tile_label"
   android:description="@string/tile_description"
   android:exported="true"
   android:permission="com.google.android.wearable.permission.BIND_TILE_PROVIDER">
   <intent-filter>
       <action android:name="androidx.wear.tiles.action.BIND_TILE_PROVIDER" />
   </intent-filter>

   <meta-data android:name="androidx.wear.tiles.PREVIEW"
       android:resource="@drawable/tile_preview" />
</service>

```

</br>

The permission and intent filter register this service as a Tile provider.

The icon, label, and description is shown to the user when they configure Tiles on their phone or watch.

</br> </br>
### Fitbit’s Fitness Tracking

There is no denying that one of the most important contributions to Fitbit’s success as a wearable brand is its great fitness tracking features. In light of that, the company will be in charge of developing features in the fitness aspect of the Wear OS. In other words, you should expect a similar user interface when accessing fitness features on the Wear OS 3.

Health features to Google Fit:

- Stress management
- Compatible ECG app
- Skin temperature
- SpO2 levels
- Sleep tracking
- Wake up


</br> </br>
## Watch Face Studio

</br>

  <img align="left" src="https://developer.android.com/images/wear/watch-face-studio_720.png" alt="Watch Free Studio" width="30%" /> Watch faces are one of the most visible ways that users can express themselves on their smartwatches. Creating a watch face is a great way to showcase your brand for users on Wear OS. Watch Face Studio (WFS) is a watch face design tool created by Samsung that allows you to produce and distribute your own watch faces without any coding. WFS includes intuitive graphics tools to allow you to easily design watch faces. Create watch faces for your personal use, or upload them in Google Play Console to share with your smartwatch users. Watch faces made using WFS can be downloaded and installed for any Wear OS watch devices, regardless of manufacturer, as long as the device targets Wear 2.0 (API level 28) or higher.
</br> </br> </br>
WFS works on both Windows and Mac environments. Here are some of the key ways you can use WFS:

- Style editing: Customize the watch face’s color, background image, font and more.
- Grouping & complications: Group components so that you can control or move those components with a single action. You can handle an entire complication as one group.
- Tag expressions: Add tags with date, time, battery, step count information and more.

</br> </br>

### Performance improvements

The unified Wear OS/Tizen (we suspect the lion’s share of this is Wear OS) will bring a 30% increase in performance, slicker animations and UI and a boost in loading times of apps.

There’s also improved battery life, but there’s no firm details on how long – but it seems it will be two days max. However, Google used the example that "includes handy optimizations like the ability to run the heart rate sensor continuously during the day, track your sleep overnight and still have battery for the next day.” We told you to temper your excitement.

</br> </br>

### Wear OS 3 has promising upgrades

In Wear OS 3, there are some promising upgrades that might entice developers to go back and design for the platform. It will get updates from time to time. Probably not as often as Android phones, though. Updates are also fairly hands-off. When you power on your phone, it will check for Wear OS updates if the Wear OS app is installed.

If there is one available, it’ll send that update to the watch the next time you connect it. If you have an LTE-capable Wear OS watch, then updates will come through to the watch as it will have a constant connection.

</br> </br>

## Recent Market Updates:

Wear OS captures 17% of the smartwatch market following strong Galaxy Watch 4 sales. Google’s Wear OS sat mostly stagnant for a few years, leading to the platform being just a footnote in the overall smartwatch market. However, thanks to strong Galaxy Watch 4 sales, Wear OS has been catapulted into second place when it comes to market share of smartwatches sold in Q3 2021.

Counterpoint Research reports that Wear OS captured 17% of smartwatch shipments in Q3 2021, up from just 4% the previous quarter. The obvious reason for this massive leap is that Wear OS now powers Samsung’s Galaxy Watch 4 series, albeit with a relatively heavy skin on top of the experience.

Samsung’s new smartwatch reportedly made up nearly 60% of smartwatch shipments in North America and Europe during Q3 2021, while Apple’s share of the market dropped significantly in Q3 due to the delayed launch of the Apple Watch Series 7.

</br> </br>

## No Killer App = Killer Opportunity For Developers

While analysts and shareholders should be concerned about the lack of use-cases and killer apps for smartwatches, this is actually good news for developers. You could be the one to undertake such smartwatch app development, and make a mark on this emerging and untapped market.

I have already talked about long-term forecasts, and the potential is clearly there. And, while we are still in the very early stages of smartwatch development, I believe this niche is worth exploring. It’s not just for risk-takers, it’s not speculative, at least not much more speculative than any traditional mobile app project today.

So what is your decision to make great apps for Wear OS 3?  

</br> </br>

## Conclusion

The use of wearable app development is predicted to grow in the future specially with Wear OS 3. With every year, such devices become more advanced and offer a wider range of features. Wearable applications can become a great addition to our mobile app that will improve the user experience or a standalone solution with unique functionality. So it’s the high time to start developing apps for Wear OS 3 and take the benefits of this untapped market with great future and features.



