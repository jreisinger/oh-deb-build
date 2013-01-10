oh-deb-build
============

dummy line
dummy line
dummy line

description
----------

<p>
Creates deb package with supplied version. This is used mostly when
packages are build automatically (when the build number is not known before
commit), but is autogenerated by build server like Jenkins.
</p>

expected directory structure is
<pre>
- DEBIAN
    - control
    - ...
- debian
    - ...
</pre>

Where <b>DEBIAN</b> directory has to have at least control file. If the control
file contains a variable ${VERSION} ex: Version: ${VERSION} it will be 
replaced for supplied version.

Other files (postinst, prerm ...) in DEBIAN directory can use any of the fields
from control file. All the field keys will be converted to uppercase and
surrounded by ${ and }. For example Package will become ${PACKAGE}.
So if the ${PACKAGE} variable is used, it will be replaced for value found in
control file.

<b>debian</b> directory should contain files that will be packaged as deb.

install
-------
<pre><code>
sudo install oh-deb-build /usr/local/bin/
</code></pre>

or to generate deb package

<pre><code>
./build <build_number>
</code></pre>

dependencies
------------
- uses <code>dpkg-deb --build</code> command to build package
