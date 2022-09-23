# Namespaces

Namespaces are used in conjunction with addon IDs to uniquely identify an addon as well as
an identifier for repositories.

## Format

Namespaces MUST only contain lowercase alphanumeric characters, hyphens (SHOULD be avoided) and dots. 
They SHOULD be in a reversed domain name format. A namespace SHOULD specify the distribution source
(i.e. `com.example.repository`) or the author (i.e. `com.author.website`) of the addon and 
optionally also the addon type (i.e. `com.example.repository.mods`, `com.author.website.modpacks`).

## Repository Namespaces

A repository namespace describes an addon repository across [API instances](../api/). A repository
contains different addons and MAY be hosted on multiple API instances (mirrors). The ID of an addon
MUST be unique in a repository, so an addon can be resolved by the addon ID in conjuction with the
repository namespace. Since the same addon MAY be contained in multiple repositories, it MUST have a
[canonical namespace](#canonical-namespaces), so it can be identified globally. The repository
described by the canonical namespace of an addon MUST also contain that addon. If different API
instances return contradicting information about a repository, for example an addon with the same
ID in the same repository has different canonical namespaces on different instances, the AddonScript
implementation decides, which instance is more trustworthy. This MAY be done by comparing the
repository namespace to the API URL or by asking the user.

## Canonical Namespaces

While an addon MAY be included in multiple repository namespaces, it MUST have exactly 
one canonical namespace, which is defined in the [addon manifest](../schema/manifest.md#namespace).
An [API instance](../api/) MUST also return the canonical namespace of 
the addon on the [addon endpoint](../api/features/addons.md#get-addon)
even if the addon was requested from another repository namespace. To check, if two addons
are the same addon, their canonical namespace and their ID MUST be equal.