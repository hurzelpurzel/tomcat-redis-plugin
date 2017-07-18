# tomcat-redis-plugin
This plugin enables a set of tomcat 8 instances to use the same session store based on redis.
This could be useful for sharing session infos for load balancing without sticky sessions.


Copy of https://github.com/jcoleman/tomcat-redis-session-manager 
Just enable Tomat 8 Classloading.
For infos about Redis Key-Value store see
http://openmymind.net/2012/1/23/The-Little-Redis-Book/


# Tomcats context.xml
Following entry must be made in Tomcat context.xml to enable Redis session
```
<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />
<Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager"
         host="localhost" <!-- optional: defaults to "localhost" -->
         port="6379" <!-- optional: defaults to "6379" -->
         database="0" <!-- optional: defaults to "0" -->
         maxInactiveInterval="60" <!-- optional: defaults to "60" (in seconds) -->
         sessionPersistPolicies="PERSIST_POLICY_1,PERSIST_POLICY_2,.." <!-- optional -->
         sentinelMaster="SentinelMasterName" <!-- optional -->
         sentinels="sentinel-host-1:port,sentinel-host-2:port,.." <!-- optional --> />

```
