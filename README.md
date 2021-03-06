# Kontent recommendation Javascript SDK

[![No Maintenance Intended](https://unmaintained.tech/badge.svg)](http://unmaintained.tech/)
## :warning: Deprecation Notice
> Kontent's Recommendations API has been deprecated (see [changelog](https://docs.kontent.ai/changelog/product-changelog#a-deprecating-the-smart-recommendations-api)). We advise to use the underlying [Recombee](https://www.recombee.com/) service directly to recommend your content. 


Javascript SDK for the `Kontent Recommendation SDK`. Works in `node.js` and `browsers`.

## Getting started

To get started, you'll first need to have access to your [Kentico Kontent](https://kontent.ai/) project and setup recommendation.

### Installation

```
npm i rxjs --save
npm i @kentico/kontent-recommendations --save
```

### API

#### Recommend Items 

```typescript
const client = new RecommendationClient({
    projectId: 'xxx',
    apiKey: 'yyy'
});

 await client.recommendItems()
    .withData({
        currentItemCodename: 'x',
        requestedTypeCodename: 'y',
        responseLimit: 5,
        visitId: 'z',
        recommendationSettings: {
            // settings configuration
        }
        }).toPromise();
```

#### Track Conversion 

```typescript
const client = new RecommendationClient({
    projectId: 'xxx',
    apiKey: 'yyy'
});

await client.trackConversion()
    .withData({
        visitId: 'z',
        currentItemCodename: 'x'
    }).toPromise();
```

#### Track Portion 

```typescript
const client = new RecommendationClient({
    projectId: 'xxx',
    apiKey: 'yyy'
});

await client.trackPortion()
    .withData({
        visitId: 'z',
        currentItemCodename: 'x',
        portionPercentage: 50
    }).toPromise();
```

#### Track Visit 

```typescript
const client = new RecommendationClient({
    projectId: 'xxx',
    apiKey: 'yyy'
});

await client.trackVisit()
    .withData({
        visitId: 'z',
        currentItemCodename: 'x',
    }).toPromise();
```

#### Track Visitor 

```typescript
const client = new RecommendationClient({
    projectId: 'xxx',
    apiKey: 'yyy'
});

await client.trackVisitor()
    .withData({
        visitId: 'x',
        visitor: {
            ip: 'y',
            custom: 'c',
            location: {
                city: 'LA',
                country: 'US',
                timezone: 'PST'
            },
            referer: 'x'
        }
    }).toPromise();
```

If you are using `UMD` bundles directly in browsers, you can find this library under `KontentRecommendation` global variable. 


### Configuration

The `RecommendationClient` contains several configuration options:

```typescript
const client = new RecommendationClient({
    // configuration options
});
```

| Option  | Default | Description |
| ------------- | ------------- | ------------- |
| `projectId` | N/A | **Required** - Id of your Kentico Kontent project  |
| `apiKey` | N/A  | **Required** - Recommendation API Token  |
| `baseUrl` | https://recommend.kontent.ai/api/v2/  | Base URL of REST api. Can be useful if you are using custom proxy or for testing purposes. |
| `retryStrategy` | undefined |  Retry strategy configuration. If not set, default strategy is used. |
| `httpService` | HttpService  | Used to inject implementation of `IHttpService` used to make HTTP request across network. Can also be useful for testing purposes by returning specified responses. |
| `isDeveloperMode` | false  | Enable to log extra details in console log|

### Troubleshooting & feedback

If you have any issues or want to share your feedback, please feel free to [create an issue](https://github.com/Kentico/kontent-recommendations-sdk-js/issues/new/choose) in this GitHub repository.

### Contributions

Contributions are welcomed. If you have an idea of what you would like to implement, let us know and lets discuss details of your PR.

