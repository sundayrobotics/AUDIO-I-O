- Your problem may be due to fragmentation of your GPU memory.You may want to empty your cached memory used by caching allocator.

import torch
torch.cuda.empty_cache()

