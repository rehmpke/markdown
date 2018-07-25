# The IE11 Canary in the mine

IE11 search issues are an issue, yes. but they are just a sign of things to come. Chrome and firefox will soon begin not supporting our old code as well.

That being said, we are not just affecting a few end users with browser compatibility issues. This is one of the first experiences some people/clients have with KCC. These in my opinion are missed opportunities **to be excellent**. This sets the tone for how students and community see and interact with the institution online. To get people through the enrollment process etc...

## Search box issue in IE11

> Appears the issue only occurs with IE11 in search box when hitting return. If you hit the magnifying icon search works fine. Or can switch to IE11 compatibility mode. Currently we only have a handful of users on campus using IE11. Most users are using IE10 or Chrome. We could look at have IE11 in compatibility mode however, that might comprise other web pages being access using IE11 on campus.
> _**– John Alverado**_
>
>> SharePoint 2010 compatibility issue with IE11—
>> Hi Jo in IT asked me to look at the home page search field not working in IE. This happened as the desktops computers updated to IE11. I found this to be an incompatibility issue with IE11 and SharePoint 2010. As I believed this to be a compatibility issue, I turned on compatibility mode in IE11 and then search works as expected.
>> _**- Roger Ehmpke**_

## Compatibility mode

### What does compatibility mode mean for SharePoint?

### How is it set in master page of a SharePoint site?

    <meta http-equiv="X-UA-Compatible" content="IE=8" />

IT can also set compatibility mode on by adding kcc.edu into the list of sites to use it through a panel in IE.

### How long will this be around?

Support for the code used to build the site is drifting [The new "End of Life" upgrade notification for IE][ef7ba5c7] and more and more issues will be popping up whether they are just IE11 problems is just the start. I foresee security issues, datasheet and workflow issues arising out of out of the dated code used in SharePoints core. I am using HTML, CSS, and Javascript from 11 years ago to get this to work. I cannot support current standards and practices. Site performance and ranking in Google and other search engines.

  [ef7ba5c7]: https://support.microsoft.com/en-us/kb/3123303?sd=rss&spid=14019 "Microsoft document showing end of life path for old IE versions"

## Will there be an upgrade to the current version of SharePoint in the near future?

> **Question** — Will there be an upgrade to the current share point in the future?
> _**– John Alverado**_

As SharePoint 2010 began getting close to its end of date support through Microsoft, Web services rethought SharePoint as our public facing site CMS.

SharePoint works well for intranet based sites and portals. It is not a very good solutions for public facing websites. There always has been little support or community for public facing websites in this product.

This upon many other considerations led the marketing department toward other more popular CMS solutions for Higher Ed. So we started researching what others were using.

### So where are we at now?

We looked at several web vendors but were shut down as of the budget issues with the state.
