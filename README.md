# Voice-and-Messaging-Sample-Curls

 

Contacts

•	Create Contact

curl -X POST -H "Authorization: Bearer [YOUR ACCESS TOKEN]" -H "Content-Type: application/json" -d '{"first_name":"<Alice>","last_name":"<Smith>","primary_mdn":"+15551231234"}' https://api.syniverse.com/scg-external-api/api/v1/contacts

•	Create Voice Prefer Contact

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"first_name":"<Voice>","last_name":"<Contact>","voice_preference":"<PREFER_VOICE>","primary_addr_zip":"null","primary_addr_country":null,"address_list":[{"designation":"home"}],"birth_date":null,"first_acquisition_date":null,"last_acquisition_date":null,"fast_access_1":null,"extended_attributes":null,"primary_mdn":"+15551231234"}' https://api.syniverse.com/scg-external-api/api/v1/contacts

•	Create Contact with Preferred Language – German (de)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"first_name":"<Translate>","last_name":"<Contact>","voice_preference":null,"primary_addr_zip":"null","primary_addr_country":null,"address_list":[{"designation":"mobile"}],"birth_date":null,"first_acquisition_date":null,"last_acquisition_date":null,"fast_access_1":null,"extended_attributes":null,"preferred_language":"<de>","primary_mdn":"+15551231234"}' https://api.syniverse.com/scg-external-api/api/v1/contacts

•	List Contacts

curl -X GET -H "Authorization: Bearer TOKEN"  https://api.syniverse.com/scg-external-api/api/v1/contacts

•	Edit Contact

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"first_name":"<Alice2>","last_name":"<Smith2>","version_number":"<1>"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID>}

•	Update Contact with Extended Attributes

curl -X POST -H "Authorization: Bearer TOKEN" -H 'Content-Type: application/json -d '{"version_number":<4>,"extended_attributes":"{\"<Attribute1>\":\"<Value1>\",\"<Attribute2>\":\"<Value2>\"}"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID>}

•	Update Contact with Social Handle (Facebook)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"social_handles":["fb:<Facebook_recipient_ID>@<Facebook_senderId_address>"],"version_number":"<Facebook_senderId_Version_Number>"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID>}

•	Delete Contact

curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID>}

•	Create Group
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<Group_Name>","description":"<Group_Description>"}' https://api.syniverse.com/scg-external-api/api/v1/contact_groups

•	Add Contact to Group

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"contacts":["<Contact_ID>"]}' https://api.syniverse.com/scg-external-api/api/v1/contact_groups/{Group_ID}/contacts

•	List Groups

curl  -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contact_groups

•	List Members

curl  -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contact_groups/{Group_ID}/contacts
   
•	Delete Group

curl -X DELETE  -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contact_groups/{Group_ID}

•	Create Contact Fast Access Rule

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"target_attribute_name":"<FavoriteColor2>","target_attribute":"<fast_access_12>","value_derivation_script":"<$..extended_attributes.Favorite_Color>"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/fast_access

•	List Fast Access

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contacts/fast_access

•	Delete Contact Fast Access Rule

curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/contacts/fast_access/{Rule_ID}
 
  
Messaging
   
•	List Sender IDs

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids 

•	Delete SenderID

curl -X DELETE  -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids/{Sender_ID}

•	Create SenderID (Shortcode)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<SenderId_Name>","class_id":"COMMERCIAL","type_id":"SHORTCODE","address":"<22222>","country":"<USA>", "consent_managed_by":"USER", "capabilities":["SMS"]}' https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids

•	CreateSenderID with Consent (Shortcode)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<SenderId_Name>","class_id":"COMMERCIAL","type_id":"SHORTCODE","address":"<22222>","country":"<USA>", "consent_managed_by":"SCG", "capabilities":["SMS"]}' https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids

•	Create Channel

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<Channel_Name>","description":"<Channel_Description>","priority":"<HIGH>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/channels

•	Add SenderId to a Channel

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"sender_ids":["<senderId_ID>"]}' https://api.syniverse.com/scg-external-api/api/v1/messaging/channels/{Channel_ID}/sender_ids

•	List Channels

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/channels

•	List SenderIds associated with a Channel

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/channels/{Channel_ID}/sender_ids

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["+15551231234"],"body":"<Hello World>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message Using Template

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["+15551231234"],"body":"<#set($Brand_name=\"Kongo\")\n#set($Ref_Number=\"3jsdfj\")\n#set($link=\"http://example.com/asdfasd\")\n#parse(\"Shipping_Alert\")>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message using Channel

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"channel:<channel_ID>","to":["+15551231234"],"body":"<Hello World from Channel>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message to multi-recipients

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["+15551115555","+15551231234"],"body":"<Hello World>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message to Contact

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["contact:<Contact_ID>"],"body":"<Hello World to Contact>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message To a Group

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["group:<Group_ID>"],"body":"<Hello World to Group>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message to Contact with translation based on the Contact language setting

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["contact:<Contact_ID>"],"src_language":null,"dst_language":null,"translate":true,"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"test message","attachments":[],"content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Message to Contact with translation specified as Italian (it)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["+15551231234"],"src_language":"en","dst_language":"it","translate":true,"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"test message","attachments":[],"content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send MMS message

Create an Attachment (Returns Attachment ID) 
curl -X POST -H 'Authorization: Bearer TOKEN’ -H 'Content-Type: application/json;charset=UTF-8' --data-binary '{"name":"<Image2>","type":"<image/jpeg>","filename":"<Attachment_file_name.jpg>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/attachments

Send MMS Message with the Attachment

curl -X POST -H 'Authorization: Bearer TOKEN' -H 'Content-Type: application/json;charset=UTF-8' --data-binary '{"from":”<MMS_Capable_senderId_ID>“,"to":["+15551231234"],"body":"<Sent attachment>","attachments":["<attachment_ID>"],"pause_before_transmit":false}'  https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send TTS (Text-To-Speech) message

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Voice_Capable_senderId_ID>","to":["voice:+15551231234"],"body":"<Hello World, this text message will become a Voice message>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	View Outbox

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	   View Message Request

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests/{MessageRequest_ID}

•	Message Delivery Confirmation (MessageId)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d https://api.syniverse.com/scg-dra/proxy/messages/{Message_ID}/delivery_confirmation

Templates
   
•	Create Template

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"designation":"TEMPLATE","name":"<Test_Template_1>","pattern":"<Your test is ${testName}>"}'  https://api.syniverse.com/scg-external-api/api/v1/messaging/message_templates

•	Send Message Using the Template

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<senderId_ID>“,"to":["+15551231234"],"body":"<#set($testName=\"Sending with Template\")\n#parse(\"Test_Template_1\")>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Delete Template

curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/message_templates/{Template_ID}
      
Keywords
   
•	Create Keyword

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<Keyword_Name>","case":"SENSITIVE","value":"<Actual keyword>","sender_id":”<senderId_ID>“, "valid_to":"<2017-01-07T21:52:34.473Z>","valid_from":"<2016-01-07T21:52:34.473Z>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/keywords

•	List Keywords

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/messaging/keywords

Consent Management

•	Solicit Consent

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"address_type":"LONGCODE","address":"+15551231234", "sender_id":”<senderId_ID>“}' https://api.syniverse.com/scg-external-api/api/v1/consent/contact_address_statuses

•	List consent statues

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/consent/contact_address_statuses

•	Delete Consent Record
curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/consent/contact_address_statuses/{AddressStatus_ID}

WeChat Messaging

•	Creating a WeChat SenderID

curl --request POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"name":" <WeChat_senderId_name>","class_id":"COMMERCIAL","type_id":"WECHAT","billing":{"expiration_date":"<2027-04-05T07:00:00.000Z>"},"credentials":"{\"app_secret\":\"<WeChat_app_secret>\",\"app_id\": \"<WeChat_app_ID>\",\"token\": \"<WeChat_app_Token>}\"}","address":"<WeChat_senderId_address>"}'  https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids -v

•	Post/send a msg to WeChat account from SCG

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<WeChat_senderId_ID>","to":["we:<WeChat_recipient_ID>@<WeChat_senderId_address>"],"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"<Hello to WeChat from SCG>","attachments":[],"content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null}'  https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests -v

•	Post/send a msg to WeChat account from SCG with attachment

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<WeChat_senderId_ID>","to":["we:<WeChat_recipient_ID>@<WeChat_senderId_address>"],"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"<Hello to WeChat from SCG with attachment>","content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null,"attachments":["<Attachment_ID>"],"pause_before_transmit":false}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests -v

Facebook Messaging

•	Creating a Facebook SenderID

curl --request POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<Facebook_senderId_name>","class_id":"COMMERCIAL","type_id":"FACEBOOK","credentials":"{\"app_secret\":\"<Facebook_app_secret>\",\"page_access_token\":\"<Facebook_page_access_token>\"}"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids -v

•	Post/send a msg to Facebook account from SCG

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Facebook_senderId_ID>","to":["fb:<Facebook_recipient_ID>@<Facebook_senderId_address>"],"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"<Hello to Facebook from SCG>","attachments":[],"content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null}'  https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests -v

•	Post/send a msg to Facebook account from SCG with attachment

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Facebook_Sender_ID>","to":["fb:<Facebook_recipient_ID>@<Facebook_senderId_address>"],"test_message_flag":null,"scheduled_delivery_time":"","subject":"subject","price_threshold":null,"scheduled_delivery_time_zone":"LOCAL","expiry_time":null,"body":"<Hello to Facebook from SCG with attachment>","content_type":null,"consent_requirement":"NONE","contact_delivery_address_priority":null,"sender_id_sort_criteria":null,"attachments":["<Attachment_ID>"],"pause_before_transmit":false}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests -v

Voice Calling

•	Create a bridge.

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"bridge_audio":true}' https://api.syniverse.com/scg-external-api/api/v1/calling/bridges -v

•	List all bridges

curl -X GET -H "Authorization: Bearer TOKEN"  https://api.syniverse.com/scg-external-api/api/v1/calling/bridges -v

•	List a particular bridge

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/calling/bridges/{Bridge_ID} -v

•	Delete a Bridge

curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/calling/bridges/{Bridge_ID}

•	Make a call to the calling party 

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from”:”<Voice_senderId_ID>“,”to":"+15551231234"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls

•	Making a call to the recipient

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":"<Voice_senderId_ID>","to":"+15551231235"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls

•	Add calls to the bridge

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"call_ids":["<Calling_Party_Call_ID>", "<Recipient_Call_ID>"],"bridge_audio":true}' https://api.syniverse.com/scg-external-api/api/v1/calling/bridges/{Bridge_ID}

•	Make a call to the calling party with bridge

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from”:”<Voice_senderId_ID>“,”to":"+15551231234", "bridge_id":"<Bridge_ID>"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls -v

•	Making a call to the recipient with bridge

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":”<Voice_senderId_ID>“,"to":"+18135551212","bridge_id":"<Bridge_ID>"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls -v

•	Retrieve list of calls

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/calling/calls -v

•	Retrieve a particular call details

curl -X GET -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/calling/calls/{Call_ID} -v

•	Hangup a call:

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"state":"COMPLETED"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls/{Call_ID} -v

•	Delete a call

curl -X DELETE -H "Authorization: Bearer TOKEN" https://api.syniverse.com/scg-external-api/api/v1/calling/calls/{Call_ID}

Incoming call

•	Activate the Incoming Call
curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"state":"ACTIVE"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls/{Call_ID} -v

•	Create an Outbound call

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":”<Voice_senderId_ID>“,"to":"+15551231234"}'  https://api.syniverse.com/scg-external-api/api/v1/calling/calls

•	Create the bridge

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"bridge_audio":true}'  https://api.syniverse.com/scg-external-api/api/v1/calling/bridges -v

•	Add the calls to Bridge

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"call_ids":["<Incoming_Call_ID>", "<Outbound_Call_ID>"],"bridge_audio":true}'  https://api.syniverse.com/scg-external-api/api/v1/calling/bridges/{Bridge_ID}

Conference Calls

•	Conference creation

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":”<Voice_senderId_ID>“}' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences

•	Retrieve a particular conference details

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}

•	List all conferences

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" https://api.syniverse.com/scg-external-api/api/v1/calling/conferences

•	Conference delete

curl -X DELETE -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json"  -d '' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}

•	Conference member add
Create call 1

curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":"<Voice_Enabled_senderId_ID>","to":"+15551231231"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls

Add member1 to the conference
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"callId":"<Call1_ID>"}' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members

Create call 2
curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":”<Voice_senderId_ID>“,"to":"+15551231232"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls

Add member2 to the conference
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"callId":"<Call2_ID>"}' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members

Create call 3
curl -X POST -H "Authorization: Bearer TOKEN"  -H 'Content-Type: application/json' -d '{"from":”<Voice_senderId_ID>“,"to":"+15551231233"}' https://api.syniverse.com/scg-external-api/api/v1/calling/calls

Add member3 to the conference
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"callId":"<Call3_ID>"}' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members

•	Retrieve conference members list

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members

•	Retrieve a particular conference member details

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json"  https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members/{Member_ID}

•	Remove/Delete a member from the conference

curl -X DELETE -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '' https://api.syniverse.com/scg-external-api/api/v1/calling/conferences/{Conference_ID}/members/{Member_ID}

Push Notification

•	Create access token

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"duration":"6000"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/<Contact_ID>/access_tokens

•	List all application tokens for particular contact

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID}/application_tokens

•	List specific  application token for particular contact

curl -X GET -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID}/application_tokens/{Contact_Application_Token_ID}

•	Add application token to a contact

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"sender_id_address":"<your address>","message_delivery_provider":"<APN or GCM>","token":"<APN or GCM application token>"}' https://api.syniverse.com/scg-external-api/api/v1/contacts/{Contact_ID}/application_tokens

•	Register Token

iOS (APN)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"app_id":"<your app ID>","type":"APN","token":"<your app token>"}' https://api.syniverse.com/scg-dra/proxy/push_tokens/register

Android (GCM)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"app_id":"<your app ID>","type":"GCM","token":"<your app token>"}' https://api.syniverse.com/scg-dra/proxy/push_tokens/register

•	Unregister token

iOS (APN)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"app_id":"<your app ID>","type":"APN","token":"<your app token>"}' https://api.syniverse.com/scg-dra/proxy/push_tokens/unregister

Android (GCM)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"app_id":"<your app ID>","type":"GCM","token":"<your app token>"}' https://api.syniverse.com/scg-dra/proxy/push_tokens/unregister

•	Delete Token

curl -X DELETE -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d   https://api.syniverse.com/scg-external-api/api/v1/contacts/<Contact_ID>/application_tokens/{Contact_Application_Token_ID}

•	Create Sender address for Push Notification (Both APN and GCM)

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"name":"<Push_senderId_Name>","class_id":"COMMERCIAL","type_id":"PUSH","address":"<address of your app example:com.syniverse.scg.push.demo>","capabilities":["PSH"],"credentials":"{\"APN\":{\"certificate\":\"<APN_Certificate_Value>\",\"topic\":\"<topic of your app example:com.syniverse.scg.push.demo>\",\"environment\":\"<sandbox or production>\"},\"GCM\":{\"certificate\":\"<GCM_Certificate_Value>\"} }" }' https://api.syniverse.com/scg-external-api/api/v1/messaging/sender_ids

•	Send Push Notification to Contact

curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Push_senderId_ID>","to":["contact:<Contact_ID>"],"body":"<Hello Push  test>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests

•	Send Push Notification to Token

iOS (APN)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Push_senderId_ID>","to":["psh:apn@<Push_senderId_ID>@<your app token>"],"body":"<Hello Push to Token – APN>"}' https://api-int.syniverse.com/scg-external-api/api/v1/messaging/message_requests

Android (GCM)
curl -X POST -H "Authorization: Bearer TOKEN" -H "Content-Type: application/json" -d '{"from":"<Push_senderId_ID>","to":["psh:gcm@<Push_senderId_ID>@<your app token>"],"body":"<Hello Push to Token – GCM>"}' https://api.syniverse.com/scg-external-api/api/v1/messaging/message_requests


