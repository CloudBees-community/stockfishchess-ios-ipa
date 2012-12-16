stockfishchess-ios-app
======================

Stockfish iOS app: Automated CI for iOS (Universal iPhone/iPad build) using CloudBees/Jenkins.  Based on Mukul Sharma's [port](https://github.com/elitecoder/stockfishchess-ios) of the [Stockfish](http://stockfishchess.org) chess engine.  This build runs on a MacOS slave, using the [Customer Provided Executors](https://wiki.cloudbees.com/bin/view/DEV/Customer+Provided+Slaves) feature of ClousBees DEV@Cloud.  Please consult the [CloudBees documentation](https://wiki.cloudbees.com/bin/view/DEV/Customer+Provided+Slaves) for how to configure and connect the slave - you will need to set up ssh keys to secure the connection, which can be started like this:

<i>java -jar jenkins-cli.jar -s https://&lt;your-domain-name&gt;.ci.cloudbees.com -i &lt;your-private-ssh-keyfile&gt; customer-managed-slave -fsroot &lt;Jenkins-workspace-location&gt; -labels android -labels xcode -executors 4 -name mobile-slave</i>

<a href="https://grandcentral.cloudbees.com/?CB_clickstart=https://raw.github.com/mqprichard/stockfishchess-ios-app/master/clickstart.json"><img src="https://d3ko533tu1ozfq.cloudfront.net/clickstart/deployInstantly.png"/></a>

You will need to have Xcode installed on the MacOS slave: this build will produce an .ipa archive, which can be installed to a locally-tethered device, or distributed for beta testing via the TestFlight/Appaloosa Jenkins plugins (requires an ad hoc Provisioning Profile to be configured on the slave). The archive is generated in: <i>$WORKSPACE/build/${Configuration}-${SDK)</i>. 

See this [CloudBees blog](http://blog.cloudbees.com/2012/12/mobile-builds-with-jenkins-in-cloud.html) for more information
