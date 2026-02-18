mvn archetype:generate -DgroupId=co.logike -DartifactId=archetype-pwa -DarchetypeArtifactId=maven-archetype-archetype

mvn archetype:generate -DarchetypeGroupId=co.logike -DarchetypeArtifactId=archetype-pwa -DarchetypeVersion=1.0.0-SNAPSHOT


mvn archetype:generate -B -DarchetypeGroupId=co.logike -DarchetypeArtifactId=archetype-pwa -DarchetypeVersion=1.0.0-SNAPSHOT -DgroupId=co.logike -Dpackage=co.logike -DartifactId=test-pwa -DfeatureName=Persona -DfeatureNameFolder=persona/gestion -Demail=javier.latorre@logike.co -Dautor=Javier_Latorre -DprojectName=TestPWA -Dtheme=thema Dversion=1.0.0-SNAPSHOT 

mvn archetype:generate -B \
  -DarchetypeGroupId=co.logike \
  -DarchetypeArtifactId=archetype-pwa \
  -DarchetypeVersion=1.0.0-SNAPSHOT \
  -DgroupId=co.logike \
  -DartifactId=test-pwa  \
  -Dversion=1.0.0-SNAPSHOT \
  -Dpackaging=jar \
 -DfeatureName=Persona \
 -Demail=javier.latorre@logike.co \
 -Dautor=Javier Latorre \
 -DprojectName=TestPWA \
 -Dtheme=Mytheme \
 -Dname=Test PWA \

mvn archetype:generate -B -DarchetypeGroupId=co.logike -DarchetypeArtifactId=archetype-pwa -DarchetypeVersion=1.0.0-SNAPSHOT -DgroupId=co.logike -Dpackage=co.logike -DartifactId=test-pwa -DfeatureName=Persona -DfeatureNameFolder=persona/gestion -Demail=javier.latorre@logike.co -Dautor=Javier_Latorre -DprojectName=TestPWA -Dtheme=thema -Dname=TestPWA -Dpackaging=jar