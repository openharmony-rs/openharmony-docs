# __ani_vm

## Overview

**System capability**: SystemCapability.ArkCompiler.ANI

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const struct \_\_ani_vm_api *c_api |  |
| ani_status DestroyVM()
    {
        return c_api->DestroyVM(this);
    }
    ani_status GetEnv(uint32_t version, ani_env **result)
    {
        return c_api->GetEnv(this, version, result);
    }
    ani_status AttachCurrentThread(const ani_options *options, uint32_t version, ani_env **result)
    {
        return c_api->AttachCurrentThread(this, options, version, result);
    }
    ani_status DetachCurrentThread()
    {
        return c_api->DetachCurrentThread(this);
    } |  |


