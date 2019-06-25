<project name="mstest" basedir=".">
<property file="${basedir}/build.properties"/>
<property name="dist" value="dist"/>
<property name="build" value="build"/>
<property name="dist-location" value="${basedir}/${build}/${dist}"/>
<property environment="env" description="System environment variables (set by Jenkins)"/>
 <!--
<path id="global.classpath">
		<fileset dir="${web-inf-lib}">
			<include name="**/*.jar" />
		</fileset>
		<fileset dir="${common_lib}">
			<include name="**/*.jar" />
		</fileset>
	</path>
	
-->
<tstamp/>
<target name="init" description="Creates the required build directories">
<mkdir dir="${dist-location}"/>
</target>
<target name="clean" description="Cleans the build location">
<delete dir="${build}"/>
</target>
<target name="create-zip" depends="clean,init" description="Generates zip file">
<zip destfile="${dist-location}/deployables.zip">
<zipfileset dir="${basedir}"/>
<fileset dir="${basedir}" includes="*.txt"/>
</zip>
<echo message="awstraing zip file"/>
</target>
</project>
