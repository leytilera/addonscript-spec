# Namespaces

Namespaces are used in conjunction with addon IDs to uniquely identify an addon.

## Format

Namespaces may only contain lowercase alphanumeric characters, hyphens (should be avoided) and dots. 
They should be in a reversed domain name format. A namespace should specify the distribution source
(i.e. `com.example.repository`) or the author (i.e. `com.author.website`) of the addon and 
optionally also the addon type (i.e. `com.example.repository.mods`, `com.author.website.modpacks`).

## Canonical Namespaces

While an addon can have multiple namespaces, it must have exactly one canonical
namespace, which is defined in the [addon object](../schema/addon.md#namespace).
An [API instance](../api/) must also return the canonical namespace of 
the addon on the [addon endpoint](../api/features/addons.md#get-addon)
even if the addon was requested from another namespace. To check, if two addons
are the same addon, thier canonical namespace and their ID must be equal.

## Default Namespaces

Each [API instance](../api/) has a default namespace. Addons in the 
repository of that API instance should have that namespace, as long as there
are no ID conflicts in the repository. The default namespace does not need
to be the canonical namespace of these addons. 