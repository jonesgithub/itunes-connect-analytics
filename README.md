# itunes-connect
## What is itunes-connect
`itunes-connect` is an PHP class for pull statistics and analytics data about your iOS app from iTunes Connect.
Class emulates authorization and save authorization token when new instance is created.
Data fetched withing native iTunes Connect XHR requests and returned as associative array.

#Usage
    use icoder\iTunesConnect;

    //Pass iTunes Connect credentials to iTunesConnect class constructor
    //Replace 1011231234 with your application ID
    $itunes = new iTunesConnect('example@example.com', 'youriTunesConnectPass', 1011231234);

    //Fetch statistics data: installs, sessions, activeDevices, units, rollingActiveDevices, impressionsTotalUnique
    $allStats = $tunes->getStats(
        new DateTime('12-03-2017'),
        new DateTime('13-03-2017')
    );
    //Fetch only installs
    $installs = $tunes->getStats(
        new DateTime('12-03-2017'),
        new DateTime('13-03-2017'),
        ['installs']
    );
    //Fetch only sessions and installs
    $sessionsAndInstalls = $tunes->getStats(
        new DateTime('12-03-2017'),
        new DateTime('13-03-2017'),
        ['sessions', 'installs']
    );
    //Fetch only activeDevices with frequency week
    $activeDevicesInMonth = $tunes->getStats(
        new DateTime('01-03-2017'),
        new DateTime('07-03-2017'),
        ['activeDevices'],
        'WEEK'
    );