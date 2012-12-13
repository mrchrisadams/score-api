Versioning
==========


All URIs are versioned.

API endpoints ar hosted under `/{version}/{rest-of-path}`

The version path segment is structured like this: '{major}.{minor}.{fix}'.

For example, '1.0.0'.

The first part of the version is the major version which won't change often and any change would be significant and likely breaking.
The second part is the minor version and will change when incremental enhancements are added within the major version. Minor version changes will be non-breaking (backwards compatible) but clients may need to make changes to use newer versions.

The last part is for small fixes and may change often but will be non-breaking.

Each version number part is incremented separately and can increment to 10 and beyond. So, '3.3.12' is valid for example.
We can allow 'x' in the version string to allow the latest version of that part. So, '1.0.x' would always route to the most recent fix version but stick to the same major and minor version.
We will allow the latter parts of the version string to be omitted, for example: '1.0' & '1'.
To be clear, the first path segment of all API URIs is reserved for this version string.

All URIs described in this document are assumed to conform to the above versioning rules and to have '1.0' as the version value. Most example URIs in this document will omit the version segment.

The versioning scheme described above is similar to and perhaps a subset of SemVer.