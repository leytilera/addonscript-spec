# Namespaces

Namespaces are used in conjunction with addon IDs to uniquely identify an addon.

## Format

Namespaces MUST only contain lowercase alphanumeric characters, hyphens (SHOULD be avoided) and dots. 
They SHOULD be in a reversed domain name format. A namespace SHOULD specify the distribution source
(i.e. `com.example.repository`) or the author (i.e. `com.author.website`) of the addon and 
optionally also the addon type (i.e. `com.example.repository.mods`, `com.author.website.modpacks`).

## Canonical Namespaces

While an addon MAY have multiple namespaces, it MUST have exactly one canonical
namespace, which is defined in the [addon manifest](../schema/manifest.md#namespace).
An [API instance](../api/) MUST also return the canonical namespace of 
the addon on the [addon endpoint](../api/features/addons.md#get-addon)
even if the addon was requested from another namespace. To check, if two addons
are the same addon, their canonical namespace and their ID MUST be equal.

## Default Namespaces

Each [API instance](../api/) has a default namespace. Addons in the 
repository of that API instance SHOULD have that namespace, as long as there
are no ID conflicts in the repository. The default namespace does not need
to be the canonical namespace of these addons. 