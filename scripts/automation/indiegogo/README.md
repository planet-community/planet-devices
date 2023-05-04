# Indiegogo solutions

Most(probably all) of these rely on getting a curl command from your web browser. Instructions for getting those are below.

## Considerations

### Never share your curl command

Your curl command contains enough information for someone to at least request information about you, and almost certainly enough to make changes on your behave.

If you do accidentally share it; contact support immediately and find out how to change your access token. It may simply be a matter of logging out and in again on the browser that you originally got the curl command from. But they will know for sure.

### Interval

TL;DR Make sure you have an interval or at least 20 minutes between requests. Please be considerate so as to not ruin it for the rest of us.

Whether you use one of the solutions here, or make your own, it's really important to have a delay between requests that is many minutes long:

>  IMPORTANT: For anyone doing this. Make sure to put a large delay between checks. At the minimum it should be several minutes. If indiegogo get a lot of requests to this API call:
> 
> * It could cause excess load on the part of the system that wasn't designed for this many requests (disproportionate to their normal load.)
> * It could look-like/be-determined-as fraud/something dodgy.
> 
> If either of these are true, they will
> 
> * block the traffic they don't like. 
> * possibly block user accounts that are doing it.
> 
> Bonus points if you randomise the delay above a certain amount. Eg:
> 
> ```
> sleep $((1500 + $RANDOM % 600))
> ```
> 
> In the above example:
> 
> * The 1500 is the minimum number of seconds to wait: 25 minutes.
> * 600 is the maximum random component. (ie 1-600 seconds.)
> 
> Randomising it will make it look less like a bot.

## Getting the curl command

This is stolen from [klabs's comment](https://discord.com/channels/798562411421499392/798562411963220020/955394503898963969) on the discord chat.

1. Go to your contribution page, open network devtools
2. Search for "private_api", you should see a request with your contribution id (29xxxxxx here) as name
3. Right click on it, "Copy" menu, "Copy as cURL"
4. Create a sh script with that copied cURL command (add `-s` if you want a clean output edit: also add `--compressed` if it's not there already, it might not work without it), pipe it to jq | jq -r '.response.display_status.overall')
