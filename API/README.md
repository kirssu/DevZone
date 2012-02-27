##GetResponse API Documentation
version 1.8.10, 2012-01-19 
[changelog](https://github.com/GetResponse/DevZone/blob/master/API/changelog.txt "changelog")

##AUTHORS
The GetResponse API Documentation is created and maintained by the 
*GetResponse DevZone Team*. If you wish to contact the authors, please use the 
following contact form at [GetResponse DevZone](http://dev.getresponse.com "GetResponse DevZone").

##DESCRIPTION
This document describes the syntax and usage of all API methods. 
GetResponse API is JSON-RPC based, server is located at 
`http://api2.getresponse.com`.
If you are the ***GetResponse360*** user please be aware that your `API URL` 
is unique and it will be provided to you by your Account Manager.

##API KEY
In order to use GetResponse API, the unique `API KEY` is required. The key 
is assigned to every pro account and you can obtain it in **My Account** section
after logging in, to your GetResponse account.

**Warning**: Please note that the `API KEY` unambiguously identifies your account 
and allows all who know the `API KEY` to manage contacts, messages etc. Please 
keep your `API KEY` safe and do not share it with any unauthorized persons.

If you are a developer and you want to utilize our API with a free account 
please use the contact form, provide us with your free account name and briefly 
describe the purpose of your project (requests without project description will 
be rejected)- we will assign the `API KEY` for you.

##SUPPORT
If you run into an error or you will have difficulties with using the API, you 
may easily report it in the Issues section here in GetResponse GitHub Organization 
profile and we will provide all the support we can to solve your problems.

##GETTING STARTED
Examples in popular programing languages are available here on 
[GetResponse GitHub](https://github.com/mgorski/DevZone/tree/master/API/examples "Examples of use") 
Including: C#, Java, JavaScript, Perl, PHP, Python, Ruby, Flex.

##METHODS

####Connection testing

* [ping](#ping)

####Account

* [get_account_info](#get_account_info)
* [get_account_from_fields](#get_account_from_fields)
* [get_account_from_field](#get_account_from_field)
* [add_account_from_field](#add_account_from_field)
* [get_account_domains](#get_account_domains)
* [get_account_domain](#get_account_domain)

####Campaigns

* [get_campaigns](#get_campaigns)
* [get_campaign](#get_campaign)
* [add_campaign](#add_campaign)
* [get_campaign_domain](#get_campaign_domain)
* [set_campaign_domain](#set_campaign_domain)
* [delete_campaign_domain](#delete_campaign_domain)
* [get_campaign_postal_address](#get_campaign_postal_address)
* [set_campaign_postal_address](#set_campaign_postal_address)

####Messages

* [get_messages](#get_messages)
* [get_message](#get_message)
* [get_message_contents](#get_message_contents)
* [get_message_stats](#get_message_stats)
* [send_newsletter](#send_newsletter)
* [add_follow_up](#add_follow_up)
* [add_draft](#add_draft)
* [delete_newsletter](#delete_newsletter)
* [delete_follow_up](#delete_follow_up)
* [set_follow_up_cycle](#set_follow_up_cycle)
* [get_messages_amount_per_account](#get_messages_amount_per_account)
* [get_messages_amount_per_campaign](#get_messages_amount_per_campaign)

####Contacts

* [get_contacts](#get_contacts)
* [get_contact](#get_contact)
* [set_contact_name](#set_contact_name)
* [get_contact_customs](#get_contact_customs)
* [set_contact_customs](#set_contact_customs)
* [get_contact_geoip](#get_contact_geoip)
* [get_contact_opens](#get_contact_opens)
* [get_contact_clicks](#get_contact_clicks)
* [set_contact_cycle](#set_contact_cycle)
* [add_contact](#add_contact)
* [move_contact](#move_contact)
* [delete_contact](#delete_contact)
* [get_contacts_deleted](#get_contacts_deleted)
* [get_contacts_subscription_stats](#get_contacts_subscription_stats)
* [get_contacts_amount_per_account](#get_contacts_amount_per_account)
* [get_contacts_amount_per_campaign](#get_contacts_amount_per_campaign)

####Links

* [get_links](#get_links)
* [get_link](#get_link)

####Blacklists

* [get_account_blacklist](#get_account_blacklist)
* [add_account_blacklist](#add_account_blacklist)
* [delete_account_blacklist](#delete_account_blacklist)
* [get_campaign_blacklist](#get_campaign_blacklist)
* [add_campaign_blacklist](#add_campaign_blacklist)
* [delete_campaign_blacklist](#delete_campaign_blacklist)

####Suppressions

* [get_suppressions](#get_suppressions)
* [get_suppression](#get_suppression)
* [add_suppression](#add_suppression)
* [delete_suppression](#delete_suppression)
* [get_suppression_skiplist](#get_suppression_skiplist)
* [add_suppression_skiplist](#add_suppression_skiplist)
* [delete_suppression_skiplist](#delete_suppression_skiplist)

####Confirmation

* [get_confirmation_subjects](#get_confirmation_subjects)
* [get_confirmation_subject](#get_confirmation_subject)
* [get_confirmation_bodies](#get_confirmation_bodies)
* [get_confirmation_body](#get_confirmation_body)
 
---

####ping<a name="ping"/>

Test connection with API.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "ping" : "pong"
    }
```

---

####get_account_info<a name="get_account_info"/>

Get basic info about your account.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "login"         : "my_login",
        "from_name"     : "My From Name",
        "from_email"    : "me@emailaddress.com",
        "created_on"    : "2010-01-01"
    }
```

---

####get_account_from_fields<a name="get_account_from_fields"/>

Get list of email addresses assigned to account.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "FROM_FIELD_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "email"         : "me@emailaddress.com",
            "name"          : "My From Name"
        },
        "FROM_FIELD_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "email"         : "also.me@another-emailaddress.com",
            "name"          : "My Other Name"
        }
    }
```

---

####get_account_from_field<a name="get_account_from_field"/>

Get single email address assigned to account using `FROM_FIELD_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "account_from_field"    : "FROM_FIELD_ID"
        }
    ]
```
Conditions:

* `account_from_field` (mandatory) – `FROM_FIELD_ID`.

_JSON result:_

```json
    {
        "FROM_FIELD_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "email"         : "me@emailaddress.com",
            "name"          : "My From Name"
        }
    }
```

---

####add_account_from_field<a name="add_account_from_field"/>

Assign email address to account. It can be used in newly created campaigns.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "name"    : "My other other name",
            "email"   : "and.me.again@my-another-emailaddress.com"
        }
    ]
```

_JSON result:_

```json
    {
        "FROM_FIELD_ID" : "abc123",
        "added"         : 1
    }
```

_JSON error messages (if any):_ `Invalid email syntax`.

**Hint**: When you add from field from web interface clicking confirmation link is required. But when you use API then it is confirmed by default and ready to use.

---

####get_account_domains<a name="get_account_domains"/>

Get domains assigned to account using www interface.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "ACCOUNT_DOMAIN_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "domain"        : "emailaddress.com"
        },
        "ACCOUNT_DOMAIN_ID" : {
            "created_on"    : "2009-01-02 00:00:00",
            "domain"        : "otheremailaddress.com"
        }
    }
```

**Warning**: Please note that after you add domain using www interface it takes up to 24h for us to check DNS propagation. So your domain may not be visible in API method output instantly.

---

####get_account_domain<a name="get_account_domain"/>

Get single domain assigned to account using www interface. Comes in handy when you need to check which domain has campaign assigned.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "account_domain"    : "ACCOUNT_DOMAIN_ID"
        }
    ]
```

_JSON result:_

```json
    {
        "ACCOUNT_DOMAIN_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "domain"        : "emailaddress.com"
        }
    }
 ```

---

####get_campaigns<a name="get_campaigns"/>

Get list of campaigns in account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "name"  : { "OPERATOR" : "value" }
        }
    ]
```

Conditions:

* `name` (optional) – Use [text operators](#operators) to narrow down search results to specific campaign names.

_JSON result:_

```json
    {
        "CAMPAIGN_ID" : {
            "name"              : "my_campaign_1",
            "description"       : "My campaign",
            "from_name"         : "My From Name",
            "from_email"        : "me@emailaddress.com",
            "reply_to_email"    : "replies@emailaddress.com",
            "created_on"        : "2010-01-01 00:00:00"
        },
        "CAMPAIGN_ID" : {
            "name"              : "my_campaign_2",
            "description"       : null,
            "from_name"         : "My From Name",
            "from_email"        : "me@emailaddress.com",
            "reply_to_email"    : "replies@emailaddress.com",
            "created_on"        : "2010-01-01 00:00:00"
        }
    }
```

**Hint**: There can be only one campaign of a given name, so if you need it’s `CAMPAIGN_ID` perform search like this:

```json
    [
        "API_KEY",
        {
            "name"  : { "EQUALS" : "your_campaign_1" }
        }
    ]
```

and the only one key from response is `CAMPAIGN_ID`.

---

####get_campaign<a name="get_campaign"/>

Get single campaign using `CAMPAIGN_ID`.
Useful for checking which campaign the contact or message belongs to.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"  : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID`.

_JSON result:_

```json
    {
        "CAMPAIGN_ID" : {
            "name"              : "my_campaign_1",
            "description"       : "My campaign",
            "from_name"         : "My From Name",
            "from_email"        : "me@emailaddress.com",
            "reply_to_email"    : "replies@emailaddress.com",
            "created_on"        : "2010-01-01 00:00:00"
        }
    }
```

---

####add_campaign<a name="add_campaign"/>

Add campaign to account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "name"                  : "my_new_campaign",
            "description"           : "My new campaign",
            "from_field"            : "FROM_FIELD_ID",
            "reply_to_field"        : "FROM_FIELD_ID",
            "confirmation_subject"  : "CONFIRMATION_SUBJECT_ID",
            "confirmation_body"     : "CONFIRMATION_BODY_ID",
            "language_code"         : "pl"
        }
    ]
```

Conditions:

* `name` (mandatory) – Value of name must be composed of lowercase letters, digits and underscores only.
* `description` (optional) – User friendly name of campaign.
* `from_field` (mandatory) – `FROM_FIELD_ID` obtained from [get_account_from_fields](#get_account_from_fields). It affects From header (name and email) in messages sent from this campaign.
* `reply_to_field` (mandatory) – `FROM_FIELD_ID` obtained from [get_account_from_fields](#get_account_from_fields). It affects Reply-To header (email) in messages sent from this campaign.
* `confirmation_subject` (mandatory) – `CONFIRMATION_SUBJECT_ID` obtained from [get_confirmation_subjects](#get_confirmation_subjects). Used in confirmation messages sent from this campaign if double-optin is set for given subscription method.
* `confirmation_body` (mandatory) – `CONFIRMATION_BODY_ID` obtained from [get_confirmation_bodies](#get_confirmation_bodies). Used in confirmation messages sent from this campaign if double-optin is set for given subscription method.
* `language_code` (optional) – Language of subscription reminder and change details / unsubscribe footer. List of available ISO 639-1 (2-letter) codes is available [here](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes). If we don’t have version in requested language then English version will be used.

_JSON result:_

```json
    {
        "CAMPAIGN_ID"   : "abc123"
        "added"         : 1
    }
```

_JSON error messages (if any):_ `Invalid email syntax`, `Name already taken`, `Missing From field`, `Missing Reply-To field`, `Missing confirmation subject`, `Missing confirmation body`.

**Warning**: Campaign added through API will be visible on www interface after next log-in.

---

####get_campaign_domain<a name="get_campaign_domain"/>

Check if any account domain is assigned to campaign. Assigned domain will be used in links in messages sent from this campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign" : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `campaigns` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).

_JSON result:_

```json
    {
        "ACCOUNT_DOMAIN_ID" : {
            "created_on"    : "2009-01-01 00:00:00",
            "domain"        : "emailaddress.com"
        }
    }
```

Empty result means that no domain is assigned.

_JSON error messages (if any):_ `Missing campaign`.

---

####set_campaign_domain<a name="set_campaign_domain"/>

Assign account domain to campaign. Assigned domain will be used in links in messages sent from this campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"          : "CAMPAIGN_ID",
            "account_domain"    : "ACCOUNT_DOMAIN_ID"
        }
    ]
```

Conditions:

* `campaigns` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).
* `account_domain` (mandatory) – `ACCOUNT_DOMAIN_ID` obtained from [get_account_domains](#get_account_domains).

_JSON result:_

```json
    {
        "updated" : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Missing account domain`.

**Warning**: Any messages sent from now on from this campaign will use this domain in links, even if message was scheduled before domain assignment.

---

####delete_campaign_domain<a name="delete_campaign_domain"/>

Detach account domain from campaign. Unassigned domain will no longer be used in links in messages sent from this campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"  : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `campaigns` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).

_JSON result:_

```json
    {
        "updated" : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`.

**Hint**: This does not delete domain from account. Domain is still visible in get_account domain result.

**Warning**: Any messages sent from now on from this campaign will not use this domain in links, even if message was scheduled before domain assignment was deleted.

---

####get_campaign_postal_address<a name="get_campaign_postal_address"/>

Get postal address and postal design (formatting) in campaign. Postal address is attached to every message sent from campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"  : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `campaigns` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).

_JSON result:_

```json
    {
        "name"      : "My name",
        "address"   : "My address",
        "city"      : "My city",
        "state"     : "My state",
        "zip"       : "My zip",
        "country"   : "My country",
        "design"    : "[[name]], [[address]], [[city]], [[state]] [[zip]], [[country]]"
    }
```

Empty result means that no postal address is assigned to domain. In such cases postal address from account is used. Fields `name` and `state` are optional and may not appear in response (and in design).

_JSON error messages (if any):_ `Missing campaign`.

---

####set_campaign_postal_address<a name="set_campaign_postal_address"/>

Set postal address and postal design (formatting) in campaign. Postal address is attached to every message sent from campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign" : "CAMPAIGN_ID",
            "name" : "My name",
            "address" : "My address",
            "city" : "My city",
            "state" : "My state",
            "zip" : "My zip",
            "country" : "My country",
            "design" : "[[name]], [[address]], [[city]], [[state]] [[zip]], [[country]]"
        }
    ]
```

Conditions:

* `campaigns` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).
* `name` (optional) - Name of you or your company.
* `address` (mandatory) – Street and number.
* `city` (mandatory) – City.
* `state` (optional) - State or region.
* `zip` (mandatory) – Zip / postal code.
* `country` (mandatory) – Country. Name must be compatible with the one on www interface.
* `design` (mandatory) – How your postal address will be formatted. Fields above marked as mandatory must also be present in design! Do not insert HTML tags here, this will be converted in HTML part of messages automatically.

_JSON result:_

```json
    {
        "updated" : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Token missing in design`.

---

####get_messages<a name="get_messages"/>

Get messages in account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaigns"     : [ "CAMPAIGN_ID", "CAMPAIGN_ID" ],
            "get_campaigns" : { get_campaigns conditions },
            "type"          : "value",
            "subject"       : { "OPERATOR" : "value" },
            "draft_mode"    : "value"
        }
    ]
```

Conditions:

* `campaigns` / `get_campaigns` (optional) – Search only in given campaigns. Uses OR logic. If those params are not given search, is performed in all campaigns in the account. Check [IDs in conditions](#ids) for detailed explanation.
* `type` (optional) – Use "newsletter" or "follow-up" to narrow down search results to specific message types.
* `subject` (optional) – Use [text operators](#operators) to narrow down search results to specific message subjects.
* `draft_mode` (optional) – Use true or false, default is false. Switches between regular messages and drafts. Draft mode can be combined with other conditions, for example with `type` condition to get newsletter drafts only.

_JSON result:_

```json
    {
        "MESSAGE_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "type"          : "follow-up",
            "subject"       : "My follow-up",
            "day_of_cycle"  : 8,
            "flags"         : ["clicktrack", "openrate"],
            "created_on"    : "2010-01-01 00:00:00"
        },
        "MESSAGE_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "type"          : "newsletter",
            "subject"       : "My newsletter",
            "send_on"       : "2010-01-01 00:00:00",
            "created_on"    : "2010-01-01 00:00:00"
        }
    }
```

Array `flags` may be present with following items:<a name="message_flags"/>

* `clicktrack` – Clicks on links in message are counted.  Note that for the link to be click-tracked it must be also wrapped in Dynamic Content `{{LINK}}` tag. This behaves differently than WWW interface, where (for simplicity) all links are click-tracked when click-track checkbox is set.
* `subscription_reminder` – Short disclaimer is added to the message content to make sure that subscriber know why they are receiving the messages.
* `openrate` – Opened messages are counted (only if html content is present).
* `google_analytics` – Google Analytics code is appended to every link in message.

**Hint**: All merge-words in subject are returned as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.

**Hint**: If type is follow-up then `day_of_cycle` is returned and if type is newsletter then `send_on` is returned. Those fields are not present in draft mode.

**Hint**: If you need plain and HTML contents of your message use get_message_contents method.

---

####get_message<a name="get_message"/>

Get single message using `MESSAGE_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"   : "MESSAGE_ID"
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID`.

_JSON result:_

```json
    {
        "MESSAGE_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "type"          : "follow-up",
            "subject"       : "My follow-up",
            "day_of_cycle"  : 8,
            "flags"         : ["clicktrack", "openrate"],
            "created_on"    : "2010-01-01 00:00:00"
        }
    }
```

---

####get_message_contents<a name="get_message_contents"/>

Get message contents (parts).

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"   : "MESSAGE_ID"
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID`.

_JSON result:_

```json
    {
        "plain" : "Hello there",
        "html"  : "<h1>Hello</h1>there"
    }
```

**Hint**: Result may contain only `plain`, only `html` or both.

**Hint**: All merge-words in contents are [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.

---

####get_message_stats<a name="get_message_stats"/>

Get message statistics with daily resolution.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"   : "MESSAGE_ID"
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID`.

_JSON result:_

```json
    {
        "2010-01-01" : {
            "sent"      : 1024,
            "opened"    : 512,
            "clicked"   : 128,
            "bounces_user_unknown"  : 8,
            "bounces_mailbox_full"  : 2,
            "bounces_block_content" : 0,
            "bounces_block_timeout" : 0,
            "bounces_block_other"   : 1,
            "bounces_other_soft"    : 16,
            "bounces_other_hard"    : 2,
            "complaints_handled"    : 1,
            "complaints_unhandled"  : 0
        },
        "2010-01-02" : {
            "sent"      : 0,
            "opened"    : 64,
            "clicked"   : 16,
            "bounces_user_unknown"  : 0,
            "bounces_mailbox_full"  : 1,
            "bounces_block_content" : 0,
            "bounces_block_timeout" : 0,
            "bounces_block_other"   : 0,
            "bounces_other_soft"    : 2,
            "bounces_other_hard"    : 0,
            "complaints_handled"    : 1,
            "complaints_unhandled"  : 0
        }
    }
```

**Hint**: Stats are aggregated by dates of given events. Hence it is normal to have stats with `sent` equals 0 and other values positive because opens, clicks, bounces and complaints take place also during a few days after message was sent.

---

####send_newsletter<a name="send_newsletter"/>

Queue a newsletter to be sent.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"      : "CAMPAIGN_ID",
            "from_field"    : "FROM_FIELD_ID",
            "subject"       : "My newsletter",
            "contents"  : {
                "plain" : "Hello there",
                "html"  : "<h1>Hello</h1>there"
            },
            "flags" : [ "clicktrack", "openrate" ],
            "contacts"          : [ "CONTACT_ID", "CONTACT_ID" ],
            "get_contacts"      : { get_contacts conditions },
            "suppressions"      : [ "SUPPRESSION_ID", "SUPPRESSION_ID" ],
            "get_suppressions"  : { get_suppressions conditions }

        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns). Newsletter will be saved in this campaign. Note that it is not the same as selecting contacts – check contacts / get_contacts params for that.
* `from_field` (optional) – `FROM_FIELD_ID` obtained from [get_account_from_fields](#get_account_from_fields). It affects From header (name and email) in message. This value will be taken from campaign if not given.
* `subject` (mandatory) – Subject value, all merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `contents` (mandatory) – Allowed keys are `plain` and `html`, at least one is mandatory. All merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `flags` (optional) – Enables extra functionality for a message, see [message_flags](#message_flags) for available values.
* `contacts` / `get_contacts` (at least one mandatory) - Contacts that should receive a newsletter. See [IDs in conditions](#ids) for detailed explanation.
* `suppressions` / `get_suppressions` (optional) – Suppressions to use with that message. Any contact email address that matches any of the masks in those suppressions will be skipped when sending. See [IDs in conditions](#ids) for detailed explanation.

_JSON result:_

```json
    {
        "MESSAGE_ID"    : "abc123",
        "queued"        : 1,
        "contacts"      : 1024
    }
```

Value of `contacts` represents the number of unique email addresses that are set to receive this newsletter.

_JSON error messages (if any):_ `Missing campaign`, `Missing From field`, `Missing contents`, `Contacts list empty`, `Dynamic Content syntax error`, `Daily limit of newsletters exceeded`.

**Hint**: You don’t have to worry about duplicates when sending to multiple campaigns. If the same email exists in my_campaign_1 and my_campaign_2 campaigns then newsletter will be sent only once to this address (chosen randomly).

**Warning**: You can send 128 newsletters daily. Common mistake is to call API in the following manner:

```json
    [
        "API_KEY",
        {
            "subject" : "Hi John",
            ...
            "contacts" : [ "CONTACT_ID" ],
        }
    ]
```

and again…

```json
    [
        "API_KEY",
        {
            "subject" : "Hi Jessica",
            ...
            "contacts" : [ "CONTACT_ID" ],
        }
    ]
```

and again…

```json
    [
        "API_KEY",
        {
            "subject" : "Hi Bruce",
            ...
            "contacts" : [ "CONTACT_ID" ],
        }
    ]
```

If you iterate through your contact list and personalize every call then you’re doing it wrong! It can be compared to sending a group of passengers from city A to B, but every passenger travels in his own train.
Correct way of sending personalized content is to use Dynamic Content syntax (check campaign_or_contact_info section) and send newsletter once to a group of people:

```json
    [
        "API_KEY",
        {
            "subject" : "Hi {{CONTACT \"subscriber_first_name\"}}",
            ...
            "contacts" : [ "CONTACT_ID", "CONTACT_ID", "CONTACT_ID" ],
        }
    ]
```

---

####add_follow_up<a name="add_follow_up"/>

Add a follow-up to the campaign at the specific day of cycle.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"      : "CAMPAIGN_ID",
            "from_field"    : "FROM_FIELD_ID",
            "subject"       : "My follow-up",
            "contents"  : {
                "plain" : "Hello there",
                "html"  : "<h1>Hello</h1>there"
            },
            "flags" : [ "clicktrack", "openrate" ],
            "day_of_cycle" : 32
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns). Follow-up will be saved in this campaign.
* `from_field` (optional) – `FROM_FIELD_ID` obtained from [get_account_from_fields](#get_account_from_fields). It affects From header (name and email) in message. This value will be taken from campaign if not given.
* `subject` (mandatory) – Subject value, all merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `contents` (mandatory) – Allowed keys are plain and html, at least one is mandatory. All merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `flags` (optional) – Enables extra functionality for a message, see [message_flags](#message_flags) for available values.
* `day_of_cycle` – Number of days between the day when a contact subscribed to a campaign and the day when the follow-up is sent. Must be not used in existing messages and in the range of 0..1000.

_JSON result:_

```json
    {
        "MESSAGE_ID"    : "abc123",
        "added"         : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Missing From field`, `Day of cycle already used`, `Missing contents`, `Dynamic Content syntax error`.

---

####add_draft<a name="add_draft"/>

Add a draft of given message type to the campaign. Useful for autosave features.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"      : "CAMPAIGN_ID",
            "from_field"    : "FROM_FIELD_ID",
            "subject"       : "My follow-up",
            "contents"  : {
                "plain" : "Hello there",
                "html"  : "<h1>Hello</h1>there"
            },
            "flags" : [ "clicktrack", "openrate" ],
            "type"  : "follow-up"
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns). Draft will be saved in this campaign.
* `from_field` (optional) – `FROM_FIELD_ID` obtained from [get_account_from_fields](#get_account_from_fields). It affects From header (name and email) in message. This value will be taken from campaign if not given.
* `subject` (mandatory) – Subject value, all merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `contents` (mandatory) – Allowed keys are plain and html, at least one is mandatory. All merge-words should be written as [GetResponse Dynamic Content](https://github.com/GetResponse/DevZone/tree/master/DC) syntax.
* `flags` (optional) – Enables extra functionality for a message, see [message_flags](#message_flags) for available values.
* `type` – Type of draft, allowed values are newsletter and follow-up.

_JSON result:_

```json
    {
        "MESSAGE_ID"    : "abc123",
        "added"         : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Missing From field`, `Missing contents`.

**Hint**: Drafts can be obtained by using get_messages in draft mode.

---

####delete_newsletter<a name="delete_newsletter"/>

Delete newsletter from campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"   : "MESSAGE_ID"
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID` obtained from [get_messages](#get_messages) or [send_newsletter](#send_newsletter).

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Missing message`, `Message is not newsletter`, `Message send event already passed`.

**Warning**: You can delete only newsletters that have send_on date in future.

---

####delete_follow_up<a name="delete_follow_up"/>

Delete follow-up from campaign.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"   : "MESSAGE_ID"
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID` obtained from [get_messages](#get_messages) or [add_follow_up](#add_follow_up).

_JSON result:_

```json
    {
        "deleted" : 1
    }
```

_JSON error messages (if any):_ `Missing message`, `Message is not follow-up`.

---

####set_follow_up_cycle<a name="set_follow_up_cycle"/>

Set day of cycle of existing follow-up.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "message"       : "MESSAGE_ID",
            "day_of_cycle"  : 64
        }
    ]
```

Conditions:

* `message` (mandatory) – `MESSAGE_ID` obtained [get_messages](#get_messages) or [add_follow_up](#add_follow_up).
* `day_of_cycle` – Number of days between the day when a contact subscribed to a campaign and the day when the follow-up is sent. Must be not used in existing messages and in the range of 0..1000.

_JSON result:_

```json
    {
        "updated" : 1
    }
```

_JSON error messages (if any):_ `Missing message`, `Message is not follow-up`, `Day of cycle already used`.

---

####get_messages_amount_per_account<a name="get_messages_amount_per_account"/>

Get total messages amount on your account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "type"  : "value"
        }
    ]
```

Conditions:

* `type` (optional) – Use newsletter or follow-up to narrow down count results to specific message types.

_JSON result:_

```json
    {
        "ACCOUNT_ID" : 16
    }
```

---

####get_messages_amount_per_campaign<a name="get_messages_amount_per_campaign"/>

Get total messages amount in every campaign on your account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "type"  : "value"
        }
    ]
```

Conditions:

* `type` (optional) – Use newsletter or follow-up to narrow down count results to specific message types.

_JSON result:_

```json
    {
        "CAMPAIGN_ID"   : 8,
        "CAMPAIGN_ID"   : 4,
        "CAMPAIGN_ID"   : 2,
        "CAMPAIGN_ID"   : 1,
        "CAMPAIGN_ID"   : 0,
        "CAMPAIGN_ID"   : 1
    }
```

---

####get_contacts<a name="get_contacts"/>

Get list of contacts from the account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaigns"     : [ "CAMPAIGN_ID", "CAMPAIGN_ID" ],
            "get_campaigns" : { get_campaigns conditions },
            "name"          : { "OPERATOR" : "value" },
            "email"         : { "OPERATOR" : "value" },
            "created_on"    : {
                "OPERATOR"  : "value",
                "OPERATOR"  : "value"
            },
            "origin"        : "value",
            "cycle_day"     : { "OPERATOR" : "value" },
            "customs"   : [
                {
                    "name"      : "name_1_value",
                    "content"   : { "OPERATOR" : "content_1_value" }
                },
                {
                    "name"      : "name_2_value",
                    "content"   : { "OPERATOR" : "content_2_value" }
                }
            ],
            "geoip" : {
                "latitude"      : { "OPERATOR" : "latitude_value" },
                "longitude"     : { "OPERATOR" : "longitude_value" },
                "country"       : { "OPERATOR" : "country_value" },
                "country_code"  : { "OPERATOR" : "country_code_value" },
                "city"          : { "OPERATOR" : "city_value" }
            },
            "clicks"        : [ "LINK_ID", "LINK_ID" ],
            "get_clicks"    : { get_links conditions },
            "last_click_on" : {
                "OPERATOR"  : "value",
                "OPERATOR"  : "value"
            },
            "opens"         : [ "MESSAGE_ID", "MESSAGE_ID" ],
            "get_opens"     : { get_messages conditions },
            "last_open_on"  : {
                "OPERATOR"  : "value",
                "OPERATOR"  : "value"
            },
            "segmentation"  : {
                "split" : split_value,
                "pack"  : pack_value
            }
        }
    ]
```

Conditions:

* `campaigns` / `get_campaigns` (optional) – Search only in given campaigns. Uses OR logic. If those params are not given, search is performed in all campaigns within the account. Check [IDs in conditions](#ids) for detailed explanation.
* `name` (optional) – Use [text operators](#operators) to narrow down search results to specific contact names.
* `email` (optional) – Use [text operators](#operators) to narrow down search results to specific contact emails.
* `created_on` (optional) – Use [time operators](#operators) to narrow down search results to specific contact creation date. Multiple operators are allowed and logic AND is used so date range can also be expressed.
* `origin` (optional) – Narrow down search results by contacts’ origin (subscription method). Allowed values are import, email, www, panel, leads, sale, api, forward, survey, iphone.
* `cycle_day` (optional) – Use [numeric operators](#operators) to narrow down search results to specific  days of the followup cycles assigned to the contacts. To find contacts that already got day 2 message you have to use `{ "GREATER" : 2 }` as they have already reached that day. To find inactive contacts pass `{ "EQUALS" : null }` condition.
* `customs` (optional) – Use [text operators](#operators) to narrow down search results to contacts having specific customs. Uses AND logic. Note that if you need OR logic you can use MATCHES operator and use alternative in regular expression. Contacts that don’t have a custom of given name are not returned in results. If custom is multi-value then “any” junction is used: condition is true if any custom value tests true according to the operator used.
* `geo` (optional) – Use operators to narrow down search results to specific contact geo location. Precisely [text operators](#operators) are allowed for country, country_code, city, [numeric operators](#operators) are allowed for latitude and longitude (values are decimal numbers, like -54.5). Uses AND logic. Contacts that don’t have a geo location data are not returned in results.
* `clicks` / `get_clicks` (optional) – Use to narrow down search results to the contacts that clicked specific links. Uses AND logic. See [IDs in conditions](#ids) for detailed explanation.
* `last_click_on` (optional) – Use [time operators](#operators) to narrow down search results to a specific date when a contact clicked the last link. Multiple operators are allowed and logic AND is used so date range can also be expressed.
* `opens` / `get_opens` (optional) – Use to narrow down search results to contacts that opened specific messages. Uses AND logic. See [IDs in conditions](#ids) for detailed explanation.
* `last_open_on` (optional) – Use [time operators](#operators) to narrow down search results to the specific date when a contact opened the last message. Multiple operators are allowed and logic AND is used so date range can also be expressed.
* `segmentation` (optional) – Allows to fetch big results in smaller packs. Split value defines the number of packs to which contacts will be split. Group defines which pack will be returned in results. For example to get all results in 10 packs call get_contacts 10 times. Set split to 10 and increase pack from 1 to 10.

_JSON result:_

```json
    {
        "CONTACT_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "name"          : "My Contact Name",
            "email"         : "my_contact_1@emailaddress.com"
            "origin"        : "www",
            "ip"            : "1.1.1.1",
            "cycle_day"     : 32,
            "created_on"    : "2010-01-01 00:00:00"
        },
        "CONTACT_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "name"          : "My Contact Name",
            "email"         : "my_contact_2@emailaddress.com"
            "origin"        : "api",
            "ip"            : "1.1.1.1",
            "cycle_day"     : null,
            "created_on"    : "2010-01-01 00:00:00"
        }
```

**Warning**: Email is unique within a campaign, but if search is performed on multiple campaigns, one email address may occur multiple times in results.

**Hint**: Segmentation does not work as pager (LIMIT x, OFFSET y behavior in SQL) and packs are “almost equal”. That means if you perform split = 10 on result that has 1000 contacts, you will get packs containing about 100 contacts. But segmentation has two very important properties that LIMIT x, OFFSET y approach doesn’t have:

* Contacts stay in their packs forever. Contact once found in the pack 23/100 will always be located in it no matter if the list was altered. This property can be used for shard-oriented synchronization.
* Packs don’t overlap. The sum of contacts in packs 1/3, 2/3 and 3/3 is the same as in search without segmentation. This property is important if you want to parallelize operation on contacts.

---

####get_contact<a name="get_contact"/>

Get a single contact using `CONTACT_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "CONTACT_ID" : {
            "campaign"      : "CAMPAIGN_ID",
            "name"          : "My Contact Name",
            "email"         : "my_contact_1@emailaddress.com"
            "origin"        : "www",
            "ip"            : "1.1.1.1",
            "cycle_day"     : 32,
            "created_on"    : "2010-01-01 00:00:00"
        }
    }
```

---

####set_contact_name<a name="set_contact_name"/>

Set contact name.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID",
            "name"      : "name_value"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.
* `name` (mandatory) – New value of name.

_JSON result:_

```json
    {
        "updated" : 1
    }
```

_JSON error messages (if any):_  `Missing contact`.

---

####get_contact_customs<a name="get_contact_customs"/>

Get list of contact customs.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact" : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "car"   : "big",
        "bike"  : [ "blue", "white" ]
    }
```

**Hint**: If custom has more than one value (multi-value) then it will be returned as an sorted array.

---

####set_contact_customs<a name="set_contact_customs"/>

Set contact customs.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact" : "CONTACT_ID",
            "customs" : [
                {
                    "name"       : "name_1_value",
                    "content"    : "content_1_value"
                },
                {
                    "name"       : "name_2_value",
                    "content"    : "content_2_value"
                }
            ]
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.
* `customs` (mandatory) – List of one or more customs to set. Value of name must be composed of letters, digits and underscores only.

Custom of a given name is:

* removed if content value is null
* updated to new content value if already present
* added if not present

Name is case insensitive.

_JSON result:_

```json
    {
        "updated"   : 2,
        "added"     : 1,
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Missing contact`.

**Hint**: One custom name may appear multiple times in case of multi-value customs (custom must be defined as multi-value on web interface). In this case new content will be added to existing custom instead of replacing previous one.

**Hint**: If you want to remove every existing content value for multi-value customs then pass null as `content` at the beginning of method call:

```json
    "customs" : [
        {
            "name"       : "name_1_value",
            "content"    : null
        },
        {
            "name"       : "name_1_value",
            "content"    : "content_1_1_value"
        },
        {
            "name"       : "name_1_value",
            "content"    : "content_1_2_value"
        },
    ]
```
    
This will clear all content values of multi-value custom and set two new ones.

**Warning**: Custom will be silently skipped if it’s multi-value and its content is not in set of allowed values declared on web interface.

**Warning**: Custom will be silently skipped if its content does not match type declared on web interface.

---

####get_contact_geoip<a name="get_contact_geoip"/>

Get contact geo location based on IP address from which the subscription was processed.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact" : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "latitude"          : "54.35"
        "longitude"         : "18.6667",
        "country"           : "Poland",
        "region"            : "82",
        "city"              : "Gdańsk",
        "country_code"      : "PL",
        "postal_code"       : null,
        "dma_code"          : "0",
        "continent_code"    : "EU",
        "time_zone"         : "Europe/Warsaw"
    }
```

**Warning**: Geo location data is based on the IP address from which a contact subscribed, so not every contact has it (for example imported contacts do not have this information) and for some ISPs it points to where the gateway of this ISP is.

---

####get_contact_opens<a name="get_contact_opens"/>

List dates when the messages were opened by contacts.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "MESSAGE_ID"    : "2010-01-01 00:00:00",
        "MESSAGE_ID"    : "2010-01-02 00:00:00"
    }
```

Note that if a contact opened the same message multiple times, only the oldest date is listed.

---

####get_contact_clicks<a name="get_contact_clicks"/>

List dates when the links in messages were clicked by contacts.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact" : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "LINK_ID"   : "2010-01-01 00:00:00",
        "LINK_ID"   : "2010-01-02 00:00:00"
    }
```

Note that if a contact clicked the same link multiple times only oldest date is listed.

---

####set_contact_cycle<a name="set_contact_cycle"/>

Place a contact on a desired day of the follow-up cycle or deactivate a contact.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID",
            "cycle_day" : 4
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.
* `cycle_day` (mandatory) – New value of cycle day, must be in the range of 0..1000. If cycle_day is null it deactivates contact.

_JSON result:_

```json
    {
        "updated"   : 1
    }
```

_JSON error messages (if any):_ `Missing contact`.

**Warning**: Do not confuse the day of cycle with position in cycle. For example if a follow-up cycle has messages set to days 1, 2, 4, 8, 16 and you set cycle_day = 4 then a contact will get message from day 4 and not message from day 8 because it’s 4th in a row.

---

####add_contact<a name="add_contact"/>

Add contact to the list.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"  : "CAMPAIGN_ID",
            "action"    : "action_value",
            "name"      : "name_value",
            "email"     : "email_value",
            "cycle_day" : cycle_day_value,
            "ip"        : "ip_value",
            "customs"   : [
                {
                    "name"      : "name_1_value",
                    "content"   : "content_1_value"
                },
                {
                    "name"      : "name_2_value",
                    "content"   : "content_2_value"
                }
            ]
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID` obtained from [get_campaigns](#get_campaigns).
* `action` (optional) – Allowed modes are standard, insert, update. If standard mode is chosen then a new contact will be added if not already present in a given campaign otherwise existing contact will be updated including name change and customs list merge. If insert mode is chosen then a contact will be added if it doesn’t exist in a given campaign but no updates will be performed otherwise. If update is chosen then a contact will be updated if it exists in a given campaign but no inserts will be performed otherwise. Default is standard.
* `name` (optional) – Name value.
* `email` (mandatory) – Email value.
* `cycle_day` (optional) – Insert contact on a given day at the follow-up cycle. Value of 0 means the beginning of the cycle. Lack of this param means that a contact will not be inserted into cycle.
* `ip` (optional) – Contact’s IP address used for geo location. Must be given in dotted decimal format.
* `customs` (optional) – List of contact customs. In case of contact update new customs will be inserted and the existing ones will be updated with the new values. Customs not provided on this list will not be removed. Custom name must be composed using lowercase letters, digits and underscores only.

_JSON result:_

```json
    {
        "queued" : 1
    }
```

_JSON error messages (if any):_ `Invalid email syntax`, `Missing campaign`, `Contact already queued for target campaign`.

**Warning**: Adding contact is not an instant action. It will appear on your list after validation or after validation and confirmation (in case of double-optin procedure).

**Hint**: It is legal to add a contact already existing in the campaign (check action param for more details) but it is illegal to have the same email added to queue twice.

**Hint**: Optin setting is locked to double optin by default, if you want to add contacts already confirmed please contact us using this form and provide us with your campaign name and the description of your business model. We will set single optin for this campaign after short verification.

---

####move_contact<a name="move_contact"/>

Move contact from one campaign to another.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID",
            "campaign"  : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.
* `campaign` (mandatory) – `CAMPAIGN_ID` to which contact should be moved to.

_JSON result:_

```json
    {
        "updated"   : 1
    }
```

_JSON error messages (if any):_ `Missing contact`, `Missing campaign`, `Contact already exists in target campaign` (also thrown if source and target campaigns are the same).

---

####delete_contact<a name="delete_contact"/>

Delete contact.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "contact"   : "CONTACT_ID"
        }
    ]
```

Conditions:

* `contact` (mandatory) – `CONTACT_ID`.

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

**Warning**: This operation cannot be undone.

---

####get_contacts_deleted<a name="get_contacts_deleted"/>

Get deleted contacts.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaigns"     : [ "CAMPAIGN_ID", "CAMPAIGN_ID" ],
            "get_campaigns" : { get_campaigns Conditions },
            "messages"      : [ "MESSAGE_ID", "MESSAGE_ID" ],
            "get_messages"  : { get_messages Conditions },
            "email"         : { "OPERATOR" : "value" },
            "reason"        : "value",
            "created_on"    : {
                "OPERATOR"  : "value",
                "OPERATOR"  : "value"
            },
            "deleted_on"   : {
                "OPERATOR" : "value",
                "OPERATOR" : "value"
            }
        }
    ]
```

Conditions:

* `campaigns` / `get_campaigns` (optional) – Search only in given campaigns. Uses OR logic. If those params are not given search is performed in all campaigns on the account. Check [IDs in conditions](#ids) for detailed explanation.
* `messages` / `get_messages` (optional) – Search only contacts removed from given messages, this info is known for example if contact clicked unsubscribe link. Uses OR logic. Check [IDs in conditions](#ids) for detailed explanation.
* `email` (optional) – Use [text operators](#operators) to narrow down search results to specific contact emails.
* `reason` (optional) – Narrow down search results only to contacts removed due to specific reason, allowed values are: unsubscribe, user, support, automation, complaint, blacklisted, api, bounce, other.
* `created_on` (optional) – Use [time operators](#operators) to narrow down search results to specific contact creation date. Multiple operators are allowed and logic AND is used so date range can also be expressed.
* `deleted_on` (optional) – Use [time operators](#operators) to narrow down search results to specific contact deletion date. Multiple operators are allowed and logic AND is used so date range can also be expressed.

_JSON result:_

```json
    {
        'CONTACT_ID' : {
            "campaign"      : "CAMPAIGN_ID",
            "name"          : "My Contact Name",
            "email"         : "my_contact_1@emailaddress.com"
            "origin"        : "www",
            "ip"            : "1.1.1.1",
            "cycle_day"     : 32,
            "reason"        : "bounce",
            "created_on"    : "2010-01-01 00:00:00",
            "deleted_on"    : "2010-01-02 00:00:00",
        },
        'CONTACT_ID' : {
            "campaign"      : "CAMPAIGN_ID",
            "message"       : "MESSAGE_ID",
            "name"          : "My Contact Name",
            "email"         : "my_contact_2@emailaddress.com"
            "origin"        : "api",
            "ip"            : "1.1.1.1",
            "cycle_day"     : null,
            "reason"        : "other",
            "created_on"    : "2010-01-01 00:00:00",
            "deleted_on"    : "2010-01-01 00:00:00",
        }
    }
```

**Warning**: If a contact was added and removed multiple times from the same campaign it is presented only once in results with newest deleted_on date.

**Hint**: Possible reasons are: unsubscribe, user, support, automation, complaint, blacklisted, api, bounce, other, other.

**Warning**: Unsubscribe link allows contact to unsubscribe from multiple campaigns, even if message was not sent from those campaigns or to contact in those campaigns.

---

####get_contacts_subscription_stats<a name="get_contacts_subscription_stats"/>

Get contacts subscription stats aggregated by date, campaign and contact’s origin.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaigns"     : [ "CAMPAIGN_ID", "CAMPAIGN_ID" ],
            "get_campaigns" : { get_campaigns Conditions },
            "created_on"    : {
                "OPERATOR" : "value",
                "OPERATOR" : "value"
            }
        }
    ]
```

Conditions:

* `campaigns` / `get_campaigns` (optional) – Get statistics only for given campaigns. Uses OR logic. If those params are not given statistics are returned from all campaigns on the account. Check [IDs in conditions](#ids) for detailed explanation.
* `created_on` (optional) – Use [time operators](#operators) to narrow down search results to specific contact creation date. Multiple operators are allowed and logic AND is used so date range can also be expressed.

_JSON result:_

```json
    {
        "2010-01-01" : {
            "CAMPAIGN_ID"   : {
                "iphone'    : 0,
                "www"       : 32,
                "sale"      : 64,
                "leads"     : 2,
                "forward"   : 0,
                "panel"     : 4,
                "api"       : 128,
                "import"    : 0,
                "email"     : 16,
                "survey"    : 1
            },
            "CAMPAIGN_ID"   : {
                "iphone"    : 8,
                "www"       : 0,
                "sale"      : 0,
                "leads"     : 64,
                "forward"   : 0,
                "panel"     : 0,
                "api"       : 512,
                "import"    : 16,
                "email"     : 0,
                "survey"    : 0
            }
        },
        "2010-01-02"    : {
            "CAMPAIGN_ID"   : {
                "iphone"    : 0,
                "www"       : 64,
                "sale"      : 128,
                "leads"     : 8,
                "forward"   : 1,
                "panel"     : 8,
                "api"       : 1024,
                "import"    : 0,
                "email"     : 2,
                "survey"    : 8
            },
            "CAMPAIGN_ID"   : {
                "iphone"    : 0,
                "www"       : 0,
                "sale"      : 0,
                "leads"     : 128,
                "forward"   : 0,
                "panel"     : 0,
                "api"       : 2048,
                "import"    : 0,
                "email"     : 0,
                "survey"    : 0
            }
        }
    }
```

**Warning**: If  there was no subscription for any contacts origin in given day then this day is not returned.

---

####get_contacts_amount_per_account<a name="get_contacts_amount_per_account"/>

Get total contacts amount on your account.

_JSON params:_

```json
    [
        "API_KEY",
    ]
```

_JSON result:_

```json
    {
        "ACCOUNT_ID"    : 128
    }
```

---

####get_contacts_amount_per_campaign<a name="get_contacts_amount_per_campaign"/>

Get total contacts amount in every campaign on your account.

_JSON params:_

```json
    [
        "API_KEY",
    ]
```

_JSON result:_

```json
    {
        "CAMPAIGN_ID"   : 64,
        "CAMPAIGN_ID"   : 32,
        "CAMPAIGN_ID"   : 0,
        "CAMPAIGN_ID"   : 16,
        "CAMPAIGN_ID"   : 16,
        "CAMPAIGN_ID"   : 0,
        "CAMPAIGN_ID"   : 0
    }
```

---

####get_links<a name="get_links"/>

Get clicktracked links.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "messages"      : [ "MESSAGE_ID", "MESSAGE_ID" ],
            "get_messages"  : { get_messages Conditions },
            "url"           : { "OPERATOR" : "value" }
        }
    ]
```

Conditions:

* `messages` / `get_messages` (optional) – Search only in given messages. Uses OR logic. If those params are not given search is performed in all messages on the account. Check [IDs in conditions](#ids) for detailed explanation.
* `url` (optional) – Use [text operators](#operators) to narrow down search results to specific URL addresses.

_JSON result:_

```json
    {
        "LINK_ID"   : {
            "message"   : "MESSAGE_ID",
            "name"      : "My Home Page",
            "url"       : "http://myhomepage.com",
            "clicks"    : 32
        },
        "LINK_ID"   : {
            "message"   : "MESSAGE_ID",
            "name"      : "My product 1",
            "url"       : "http://myhomepage.com?product=1",
            "clicks"    : 16
        }
    }
```

**Warning**: Links will not be visible if the message that contains them did not have click-tracking enabled at the time of sending.

**Hint**: If a message was edited all links are returned in results, not only the current ones.

---

####get_link<a name="get_link"/>

Get single click-tracked link using LINK_ID.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "link"  : "LINK_ID"
        }
    ]
```

_JSON result:_

```json
    {
        "LINK_ID"   : {
            "message"   : "MESSAGE_ID",
            "name"      : "My Home Page",
            "url"       : "http://myhomepage.com",
            "clicks"    : 32
        }
    }
```

---

####get_account_blacklist<a name="get_account_blacklist"/>

Get blacklist masks on account level.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "my_contact_1@emailaddress.com" : "2010-01-01 00:00:00",
        "my_contact_2@emailaddress.com" : "2010-01-01 00:00:00"
    }
```

Format of mask can be:<a name="#mask_format">

* whole email  – xxx@yyy.zz
* local part of email- xxx@
* host part of email – @yyy.zz
* MD5 hash of email – d6dba89e8479a7049d2d7b2e5b6528ec
* ISP name – #yahoo (note the # on the beginning)

**Warning**: According to [this FAQ](http://www.espcoalition.org/MD5_Suppression_list_encryption_FAQ.pdf) MD5 hash should be generated from lowercased email, check “Why do I have to normalize email addresses prior to encrypting?” section.

---

####add_account_blacklist<a name="get_account_blacklist"/>

Adds blacklist mask on account level.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "mask"  : "mask_value"
        }
    ]
```

Conditions:

* `mask` (mandatory) – Mask to blacklist, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "added" : 1
    }
```

_JSON error messages (if any):_  `Cannot set mask` (some masks are forbidden to manage), `Invalid mask syntax`.

---

####delete_account_blacklist<a name="delete_account_blacklist"/>

Delete blacklist mask on account level.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "mask"  : "mask_value"
        }
    ]
```

Conditions:

* `mask` (mandatory) – Mask to remove from blacklist, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Cannot set mask` (some masks are forbidden to manage), `Invalid mask syntax`, `Missing mask`.

---

####get_campaign_blacklist<a name="get_campaign_blacklist"/>

Get blacklist masks on campaign level.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign" : "CAMPAIGN_ID"
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID`.

_JSON result:_

```json
    {
        "my_contact_1@emailaddress.com" : "2010-01-01 00:00:00",
        "my_contact_2@emailaddress.com" : "2010-01-01 00:00:00"
    }
```

**Hint**: Check blacklist masks for available formats.

---

####add_campaign_blacklist<a name="add_campaign_blacklist"/>

Adds blacklist mask on campaign level.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign" : "CAMPAIGN_ID",
            "mask" : "mask_value"
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID`.
* `mask` (mandatory) – Mask to blacklist, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "added" : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Cannot set mask` (some masks are forbidden to manage), `Invalid mask syntax`.

---

####delete_campaign_blacklist<a name="delete_campaign_blacklist"/>

Delete blacklist mask on campaign level.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "campaign"  : "CAMPAIGN_ID",
            "mask"      : "mask_value"
        }
    ]
```

Conditions:

* `campaign` (mandatory) – `CAMPAIGN_ID`.
* `mask` (mandatory) – Mask to remove from blacklist, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Missing campaign`, `Cannot set mask` (some masks are forbidden to manage), `Invalid mask syntax`, `Missing mask`.

---

####get_suppressions<a name="get_suppressions"/>

Get list of defined suppression lists on your account.

_JSON params:_

```json
    [
        "API_KEY"
    ]
```

_JSON result:_

```json
    {
        "SUPPRESSION_ID"    : {
            "name"          : "Rude people",
            "created_on"    : "2010-01-01 00:00:00",
        },
        "SUPPRESSION_ID"    : {
            "name"          : "Mean people",
            "created_on"    : "2010-01-01 00:00:00",
        }
    }
```

---

####get_suppression<a name="get_suppression"/>

Get single suppression using `SUPPRESSION_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "suppression"   : "SUPPRESSION_ID"
        }
    ]
```

Conditions:

* `suppression` (mandatory) – `SUPPRESSION_ID`.

_JSON result:_

```json
    {
        "SUPPRESSION_ID"    : {
            "name"          : "Rude people",
            "created_on"    : "2010-01-01 00:00:00",
        }
    }
```

---

####add_suppression<a name="add_suppression"/>

Add suppression list to your account.

This method registers named container for masks, which can be added using add_suppression_skiplist.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "name"  : "Weird people"
        }
    ]
```

Conditions:

* `name` (mandatory) – Name of your suppression list, must be unique within account.

_JSON result:_

```json
    {
        "SUPPRESSION_ID"    : abc123",
        "added"             : 1
    }
```

_JSON error messages (if any):_ `Name already used`.

---

####delete_suppression<a name="delete_suppression"/>

Delete suppression list from your account.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "suppression" : "SUPPRESSION_ID"
        }
    ]
```

Conditions:

* `suppression` (mandatory) – `SUPPRESSION_ID`.

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Missing suppression`.

**Warning**: Every mask defined within this suppression will be lost.

**Warning**: Every queued message that uses this suppression will be send as planned, but contact emails will not be filtered using masks from this suppression.

---

####get_suppression_skiplist<a name="get_suppression_skiplist"/>

Skiplist is a set of masks for suppression. If contact’s email address matches any of those masks in message that uses this suppression then it will be skipped.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "suppression"   : "SUPPRESSION_ID"
        }
    ]
```

Conditions:

* `suppression` (mandatory) – `SUPPRESSION_ID` obtained from [get_suppressions](#get_suppressions).

_JSON result:_

```json
    {
        "by.whole@email.com"                : "2010-01-01 00:00:00",
        "by.local@"                         : "2010-01-01 00:00:00",
        "@by.domain"                        : "2010-01-01 00:00:00",
        "990420c537fd46a6c2af5b00ff94cf51"  : "2010-01-01 00:00:00",
        "#by_isp"                           : "2010-01-01 00:00:00"
    }
```

_JSON error messages (if any):_ `Missing suppression`.

**Hint**: Check suppression masks for available formats.

---

####add_suppression_skiplist<a name="add_suppression_skiplist"/>

Add mask to a set of masks for suppression.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "suppression"   : "SUPPRESSION_ID",
            "mask"          : "by.whole@email.com"
        }
    ]
```

Conditions:

* `suppression` (mandatory) – `SUPPRESSION_ID` obtained from [get_suppressions](#get_suppressions).
* `mask` (mandatory) – Mask to skip, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "added" : 1
    }
```

_JSON error messages (if any):_ `Missing suppression`, `Invalid mask syntax`.

---

####delete_suppression_skiplist<a name="delete_suppression_skiplist"/>

Delete mask from a set of masks for suppression.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "suppression"   : "SUPPRESSION_ID",
            "mask"          : "by.whole@email.com"
        }
    ]
```

Conditions:

* `suppression` (mandatory) – `SUPPRESSION_ID` obtained from [get_suppressions](#get_suppressions).
* `mask` (mandatory) – Mask to delete, check [available formats](#mask_format).

_JSON result:_

```json
    {
        "deleted"   : 1
    }
```

_JSON error messages (if any):_ `Missing suppression`, `Invalid mask syntax`, `Missing mask`.

**Warning**: If any queued message uses this suppression then it will be send as planned, but contact emails will not be filtered using this masks from this suppression.

---

####get_confirmation_subjects<a name="get_confirmation_subjects"/>

Get list of available subjects for confirmation messages. They can be used in campaign settings.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "language_code" : { "EQUALS" : "en" },
        }
    ]
```

Conditions:

* `language_code` (optional) – Use [text operators](#operators) to narrow down search results to specific languages. List of available ISO 639-1 (2-letter) codes is available [here](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).

_JSON result:_

```json
    {
        "CONFIRMATION_SUBJECT_ID"   : {
            "content"       : "Please confirm subscription",
            "language_code" : "en"
        },
        "CONFIRMATION_SUBJECT_ID"   : {
            "content"       : "Proszę potwierdź subskrypcję",
            "language_code" : "pl"
        }
    }
```

---

####get_confirmation_subject<a name="get_confirmation_subject"/>

Get single subject for confirmation message using `CONFIRMATION_SUBJECT_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "confirmation_subject"  : "CONFIRMATION_SUBJECT_ID",
        }
    ]
```

Conditions:

* `confirmation_subject` (mandatory) – `CONFIRMATION_SUBJECT_ID`.

_JSON result:_

```json
    {
        "CONFIRMATION_SUBJECT_ID"   : {
            "content"       : "Please confirm subscription",
            "language_code" : "en"
        }
    }
```

---

####get_confirmation_bodies<a name="get_confirmation_bodies"/>

Get list of available bodies for confirmation messages. They can be used in campaign settings.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "language_code" : { "EQUALS" : "en" },
        }
    ]
```

Conditions:

* `language_code` (optional) – Use [text operators](#operators) to narrow down search results to specific languages. List of available ISO 639-1 (2-letter) codes is available [here](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).

_JSON result:_

```json
    {
        "CONFIRMATION_BODY_ID"  : {
            "plain"         : "Please click to confirm ...",
            "html"          : "<p>Please click to confirm ...",
            "language_code" : "en"
        },
        "CONFIRMATION_BODY_ID"  : {
            "plain"         : "Prosze kliknij aby potwierdzić ...",
            "html"          : "<p>Proszę kliknij aby potwierdzić ...",
            "language_code" : "pl"
        }
    }
```

---

####get_confirmation_body<a name="get_confirmation_body"/>

Get single body for confirmation message using `CONFIRMATION_BODY_ID`.

_JSON params:_

```json
    [
        "API_KEY",
        {
            "confirmation_body" : "CONFIRMATION_BODY_ID",
        }
    ]
```

Conditions:

* `confirmation_body` (mandatory) – `CONFIRMATION_BODY_ID`.

_JSON result:_

```json
    {
        "CONFIRMATION_BODY_ID"  : {
            "plain"         : "Please click to confirm ...",
            "html"          : "<p>Please click to confirm ...",
            "language_code" : "en"
        }
    }
```

---

##OPERATORS<a name="operators"/>

There may be several types of operators in method conditions.

Text:

* `EQUALS`, `NOT_EQUALS` – Compare text literally. Case insensitive.
* `CONTAINS`, `NOT_CONTAINS` – Compare text with wild chars. Use % for any string and _ for one character. Case insensitive.

Numeric:

* `LESS`, `LESS_OR_EQUALS`, `EQUALS`, `GREATER_OR_EQUALS`, `GREATER` – Compare numbers. Use . (dot) as decimal part separator if needed.

Time:

* `FROM`, `TO`, `AT` – Compare dates in YYYY-MM-DD format.

**Warning**: Operators must be UPPERCASED.

##IDs in conditions<a name="ids"/>

In many methods IDs may be passed to conditions. Method get_messages will be used as an example of how to do it.

```json
    [
        "API_KEY",
        {
            "campaigns"     : [ "CAMPAIGN_ID", "CAMPAIGN_ID" ],
            "get_campaigns" : { get_campaigns conditions },
            ...
        }
    ]
```

Method expects a list of campaigns in conditions to narrow down search results.
Those campaigns may be given as an array of `CAMPAIGN_ID` values obtained from [get_campaigns](#get_campaigns).

```json
    [
        "API_KEY",
        {
            "campaigns" : [ "4b1b5", "b35f2b" ]
        }
    ]
```

It will return messages from those two specific campaigns.
But s   ometimes it is faster/easier to nest get_campaigns conditions in get_messages method.

```json
    [
        "API_KEY",
        {
            "get_campaigns" : { "CONTAINS" : "my_campaign_%" }
        }
    ]
```

It will return messages from campaigns that have name beginning with my_campaign_. Pretty easy, isn’t it?

**Hint**: Nesting of conditions is also legal. For example send_newsletter conditions may contain get_contacts conditions which may contain get_links conditions which may contain get_messages conditions which may contain get_campaigns conditions. Everything in one request!

**Warning**: Do not use campaigns when you mean get_campaigns. And the other way round. Condition campaigns expects array of `CAMPAIGN_ID` values while condition get_campaigns expects get_campaigns method conditions. Same for messages/get_messages, contacts/get_contacts and others.

**Warning**: Do not provide text where ID is expected. This is incorrect.

```json
    "campaigns" : [ "my_campaign_1" ]
```