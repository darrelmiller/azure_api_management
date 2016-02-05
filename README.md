# API Management Bootcamp

## Creating your API Management Service Instance

1. Open your browser to (http://manage.windowsazure.com).

1. Select the **API Management** option in the left navigation bar.

  ![](media/alt_image1.png)

1. Click the **+ New** button to create an instance of the *Api Management service*. You must specify a unique URL for this service instance. You must also specify a name for your Organization and an administrator e-mail (this does not need to be a real e-mail address).

  > **Note**: Creating an API Management instance can take up to thirty minutes.

## Creating Your First API

1. Once your service instance is ready, select the instance and click Manage to open the Admin Portal.

  ![](media/image1.png)

1. Select the APIs option in the sidebar to add an API.

  ![](media/image2.png)

1. Go to the **Settings** tab and enter the Web API Name and the backend URL. For our sample case, we assume that our API management instance is named **sidneydemo**:

  > **Note**: Ensure that you record the URL for your API before you click the **Save** button:

  - **Web API name**: Conference Api
  - **Web service url**: http://conferenceapi.azurewebsites.net
  - Ensure that the **HTTP** option is selected.
  - Leave remaining options set to their default values.

  ![](media/alt_image2.png)

1. Got to the **Operations** tab and click the **Add Operation** link.

  ![](media/alt_image5.png)

1. On the **New Operation** screen, specify the following field values and then click the **Save** button:

  - **HTTP verb**: GET
  - **URL template**: /
  - **Display name**: *
  - Leave remaining options set to their default values.

  ![](media/alt_image6.png)

## Creating Your First Product

1. Go to the Products section using the sidebar.

  ![](media/image4.png)

1. Add a new product and ensure that you *deselect* the **Require subscription** option.

  ![](media/image5.png)

  > **Note:** Free products don’t require keys that are managed and authorized by the portal.

1. Select the **Free** product from your list of products to edit the product.

  ![](media/image6.png)

1. Click the **Add API to Product** link. Select the **Conference Api** option and then click the **Save** button.

  ![](media/image7.png)

1. Click the **Publish** button to publish the product for use.

  ![](media/alt_image3.png)

1. Open your preferred HTTP request making tool.

  > **Note:** Many tools are avilable such as Postman, Fiddler, Hurl.it and Runscope. In these examples we will use screenshots from *Postman*.

1. Make a **GET** request to the back-end API endpoint: **http://conferenceapi.azurewebsites.net/**

  ![](media/alt_image4.png)

1. Make a **GET** request to the front-end API endpoint. This is the URL you recorded earlier when you created the API. In this example, we will use the URL: **http://sidneydemo.azure-api.net/**

  ![](media/alt_image.png)

## Defining a Policy

1. Policies

![](media/image10.png)

Check the Header

![](media/image11.png)

Cleanup headers

![](media/image12.png)

Change API to use Starter Product

![](media/image13.png)

Review policy scope and select Starter

![](media/image14.png)

Click View Effective Policy

![](media/image15.png)

Request that will fail

![](media/image16.png)

Get a subscription key

![](media/image17.png)

![](media/image18.png)

Add the subscription key

![](media/image19.png)

Add the trace flag

![](media/image20.png)

Find the trace location and go and take a look

# Recap :

> We fronted and API with APIM
>
> We manipulated the message
>
> We protected the API from unauthorized and abusive usage
>
> We found out how to debug APIM behavior

## Helping Your Developer Users

![](media/image21.png)

Go to \`Sign Up Now\`

![](media/image22.png)

Reply to your confirmation email

Subscribe to a Product

![](media/image23.png)

And get your keys

![](media/image24.png)

Register an app

![](media/image25.png)

And submit to App store.

![](media/image26.png)

Publish from the admin portal

![](media/image27.png)

API Docs and Console

![](media/image28.png)

Houston, we have a problem. That’s not exactly useful documentation for the API.

You can do it all yourself, by creating custom Content pages,

![](media/image29.png)

And hooking them up to the menu.

![](media/image30.png)

![](media/image31.png)

But we would rather not re-implement the docs pages with the Try functionality.

So back to the admin portal

![](media/image32.png)

We can add operations manually

![](media/image33.png)

![](media/image34.png)

Let’s take a short detour over to policies,

![](media/image35.png)

The defined operations are now showing up as a policy scope.

![](media/image36.png)

The configured Rewrite rule is simply a policy.

Back to the Speakers Operation configuration and let us define some known responses.

![](media/image37.png)

Returning to the developer console we can see the documentation for our Speakers operation.

![](media/image38.png)

For a large API, creating all the operation descriptions could take a while. Another option is to import the operations based on an API Description language.

.Net APIs can generate an API Description language document using a library called Swash buckle.

![](media/image39.png)

Review imported operations,

![](media/image40.png)

And parameters,

![](media/image41.png)

And responses,

![](media/image42.png)

Response types are defined based on formatters available.

Swashbuckle doesn’t support representation examples out of the box unfortunately. So they need to be added manually. Unfortunately, importing an existing API doesn’t merge.

![](media/image43.png)

So, lets head back over to the developer console to see what this import gives us.

![](media/image44.png)

Getting ASP.Net Routing to sync with Swashbuckle and OpenAPI specification can be challenging. There is a risk that for a non-trivial API the effort to generate the right API description automatically and deal with merge issues, the less time saved over just manually defining the API.

A compromise is to hand craft the OpenAPI specification and then import that.

![](media/image45.png)

### Styling

![](media/image46.png)

## Security

In order to protect the origin server from direct access we need to enable security on the origin server. Change the Web service URL to use https scheme as basic auth is enabled for https for this particular API.

![](media/image47.png)

Setup the Basic Auth credentials to allow API Management to call the origin server. The password is “rocks”.

![](media/image48.png)

## User Authorization

This is used to setup the Developer Console as a Client Application

![](media/image49.png)

Click on Manage Authorization Servers

![](media/image50.png)

And then Add Authorization Server and you are presented with the “Form From Hell”

![](media/image51.png)

Fortunately, it is much easier to actually secure your API. Go back to policies.

![](media/image52.png)

Place cursor in &lt;inbound&gt; element and select &lt;validate-jwt&gt;. Update as follows

![](media/image53.png)

The next step is to build a client that can authenticate using the OAuth provider. But that is an exercise to be left to the student!

All the API Management documentation, reference materials, samples, howtos, videos and screencasts can be found at <http://aka.ms/apimrocks>
