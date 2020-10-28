# DNN Google Tag Manager Connector

This Connector extension for DNN was created by [40Fingers](https://www.40fingers.net) and [Tjeps Digital Agency](https://www.tjeps.com) 
to make it a little bit easier to use Google Tag Manager inside of DNN.

This connector was built by simply copying the Google Analytics Connector from the DNN core project, and changing
it to fit the needs of Google Tag Manager.

We will make a pull-request on DNN for it, but since we're not sure wether or not it will get into the core yet, we made a package for you to get started with.

## Prerequisits
We tested this connector on DNN 9.6.1 and DNN 9,8.0 RC1, but it's expected to starting from DNN 9.2.

## Installation
1) Download the install package from the _install folder in this branch of this repository and install in DNN as you would install any other extension.
2) Open the file SiteAnalytics.config using a text editor or the config editor in DNN
3) Add the following XML snippet:
```
<AnalyticsEngine>
    <EngineType>DotNetNuke.Services.Analytics.GoogleTagManagerEngine, DNN.Connectors.GoogleTagManager</EngineType>
    <ElementId>Head</ElementId>
    <InjectTop>False</InjectTop>
    <ScriptTemplate>
        <![CDATA[     
            <!-- Google Tag Manager -->
            <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
            new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
            j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
            'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
            })(window,document,'script','dataLayer','[GTM_ID]');</script>
            <!-- End Google Tag Manager -->
        ]]>
    </ScriptTemplate>
</AnalyticsEngine>
<AnalyticsEngine>
    <EngineType>DotNetNuke.Services.Analytics.GoogleTagManagerEngine, DNN.Connectors.GoogleTagManager</EngineType>
    <ElementId>Body</ElementId>
    <InjectTop>True</InjectTop>
    <ScriptTemplate>
        <![CDATA[     
            <!-- Google Tag Manager (noscript) --> 
            <noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-5SXBKKT"
            height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
            <!-- End Google Tag Manager (noscript) -->
        ]]>
    </ScriptTemplate>
</AnalyticsEngine>
```
4) Go to the Connectors configuration in DNN, and connect the Google Tag Manager connector. That's where you can fill in the GTM-code.

Good luck

